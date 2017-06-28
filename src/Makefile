all: build

DEPENDS_CS=$(find . -type f -name *.cs | xargs echo)

build: NumCIL.sln ${DEPENDS_CS}
	msbuild /p:Configuration=Release NumCIL.sln

nupkg: build
	if [ -d nupkg ]; then rm -rf nupkg; fi
	mkdir nupkg

nupkg/NumCIL.nupkg: NumCIL/NumCIL.nuspec nupkg
	cd NumCIL; nuget pack NumCIL.nuspec
	mv NumCIL/NumCIL.*.nupkg nupkg/NumCIL.nupkg

nupkg/NumCIL.Unsafe.nupkg: NumCIL.Unsafe/NumCIL.Unsafe.nuspec nupkg
	cd NumCIL.Unsafe; nuget pack NumCIL.Unsafe.nuspec
	mv NumCIL.Unsafe/NumCIL.Unsafe.*.nupkg nupkg/NumCIL.Unsafe.nupkg
	cd ..

pack: nupkg nupkg/NumCIL.nupkg nupkg/NumCIL.Unsafe.nupkg

deploy:
	cd nupkg; nuget push NumCIL.nuspec
	cd nupkg; nuget push NumCIL.Unsafe.nuspec


clean:
	msbuild /p:Configuration=Release /t:Clean NumCIL.sln
	find . -type d -name obj | xargs rm -rf
	find . -type d -name bin | xargs rm -rf


.PHONY: all build clean
