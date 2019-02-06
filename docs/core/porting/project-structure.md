---
title: Organizowanie projektów programu .NET Framework i .NET Core
description: Pomoc dla właścicieli projektu, którzy chcą Kompiluj swoje rozwiązanie dla platformy .NET Framework i .NET Core side-by-side.
author: conniey
ms.date: 04/06/2017
ms.custom: seodec18
ms.openlocfilehash: 4f3469c7f5c8c95cb5bf2ce522c8732c90744755
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759668"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Zorganizować projekt do obsługi środowiska .NET Framework i .NET Core

Dowiedz się, jak utworzyć rozwiązanie, które jest kompilowany dla środowiska .NET Framework i .NET Core side-by-side. Zobacz kilka opcji do organizowania projektów, aby pomóc Ci osiągnąć ten cel. Poniżej przedstawiono niektóre typowe scenariusze należy wziąć pod uwagę podczas wybierania sposobu konfigurowania układ projektu za pomocą programu .NET Core. Lista nie może obejmować wszystkie potrzebne mu; Ustaw priorytet zależnie od potrzeb Twojego projektu.

* [**Łączenie istniejących projektów i projektów .NET Core w jednym projektów**][option-csproj]

  *Co to jest dobre dla:*
  * Upraszczanie procesu kompilacji, kompilowanie pojedynczego projektu, a nie każdego przeznaczonych dla różnych wersji programu .NET Framework lub platformy kompilacji wielu projektów.
  * Upraszczanie zarządzanie plikami źródła dla projektów docelowych multi, ponieważ musisz zarządzać pliku pojedynczego projektu. Podczas dodawania/usuwania plików źródłowych, alternatyw wymagają ręcznie zsynchronizować je z innych projektów.
  * Łatwe generowanie pakietu NuGet do użycia.
  * Umożliwia pisanie kodu dla określonej wersji środowiska .NET Framework w bibliotekach przy użyciu dyrektywy kompilatora.

  *Nieobsługiwane scenariusze:*
  * Wymaga deweloperzy mogą używać programu Visual Studio 2017 można otworzyć istniejące projekty. Do obsługi starszych wersji programu Visual Studio [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.

* <a name="support-vs"></a>[**Zachowaj istniejące projekty i nowych projektów .NET Core, oddzielne**][option-csproj-folder]

  *Co to jest dobre dla:*
  * W dalszym ciągu obsługuje programowanie na istniejące projekty bez konieczności aktualizacji dla deweloperów lub współautorzy, którzy nie mają Visual Studio 2017.
  * Zmniejsza możliwości tworzenia nowych usterek w istniejących projektów, ponieważ postęp dokonany w kodzie jest wymagany w tych projektach.

## <a name="example"></a>Przykład

Należy wziąć pod uwagę poniższe repozytorium:

![Istniejący projekt][example-initial-project]

[**Kod źródłowy**][example-initial-project-code]

Poniżej przedstawiono kilka sposobów dodawania pomocy technicznej dla platformy .NET Core dla tego repozytorium, w zależności od ograniczeń i złożoność istniejących projektów.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Zamień istniejące projekty projektu .NET Core ukierunkowane na wielu

Reorganizować tak, aby każda istniejącego repozytorium  *\*.csproj* pliki są usuwane i pojedynczą  *\*.csproj* tworzony jest plik, który jest przeznaczony dla wielu platform. Jest to doskonałe rozwiązanie, ponieważ jeden projekt jest w stanie kompilowanie dla różnych platform. Ma również uprawnienia do obsługi opcji różnych kompilacji i zależności dla platformy docelowej.

![Tworzenie pliku csproj, który jest przeznaczony dla wielu platform][example-csproj]

[**Kod źródłowy**][example-csproj-code]

Zmiany, należy pamiętać, są następujące:

* Zastąpienie *packages.config* i  *\*.csproj* dzięki nowemu [platformy .NET Core  *\*.csproj* ] [ example-csproj-netcore]. Pakiety NuGet są określane za pomocą `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachowaj istniejące projekty i utworzyć projekt .NET Core

W przypadku istniejących projektów przeznaczonych dla platform starszych można pozostawić te projekty w charakterze, a przyszłe ustalać platformy docelowe za pomocą projektu .NET Core.

![Projekt .NET core z istniejącego projektu w innym folderze][example-csproj-different-folder]

[**Kod źródłowy**][example-csproj-different-code]

Zmiany, należy pamiętać, są następujące:

* .NET Core i istniejące projekty są przechowywane w oddzielnych folderach.
  * Utrzymywanie projektów w oddzielnych folderach pozwala uniknąć, co zmuszało do programu Visual Studio 2017. Możesz utworzyć oddzielne rozwiązanie, które otwiera tylko starych projektów.

## <a name="see-also"></a>Zobacz także

Zobacz [platformy .NET Core, przenoszenie dokumentacji] [ porting-doc] Aby uzyskać więcej wskazówek na temat migracji do platformy .NET Core.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Istniejący projekt"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Tworzenie pliku csproj, który jest przeznaczony dla wielu platform"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projekt .NET core przy użyciu istniejących PCL w innym folderze"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
