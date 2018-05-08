---
title: Organizowanie projektu do obsługi środowiska .NET Framework i .NET Core
description: Pomoc dotyczącą właściciele projektu do skompilowania ich rozwiązanie przed .NET Framework i side-by-side .NET Core.
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.openlocfilehash: e6cd9c6d66996d9fd24fe71d48091723143e5849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>Organizowanie projektu do obsługi środowiska .NET Framework i .NET Core

W tym artykule opisano właściciele projektu do skompilowania ich rozwiązanie przed .NET Framework i side-by-side .NET Core. Zapewnia kilka opcji do organizowania projektów, aby pomóc deweloperom osiągnięcie tego celu. Poniżej przedstawiono niektóre typowe scenariusze wziąć pod uwagę, gdy jest o wyborze sposobu instalacji układ projektu z platformą .NET Core. Lista nie może obejmować wszystkie potrzebne; priorytet oparte na potrzeby projektu.

* [**Łączenie istniejących projektów i .NET Core projektów w jednym projektów**][option-csproj]

  *Co to jest dobre dla:*
  * Uproszczenie procesu kompilacji, kompilowanie pojedynczego projektu zamiast kompilowanie wielu projektów każdy przeznaczonych dla różnych wersji programu .NET Framework lub platformy.
  * Uproszczenie zarządzania plikami źródła dla projektów docelowe multi, ponieważ muszą zarządzać tworzenia projektów. Podczas dodawania/usuwania plików źródłowych, alternatywnych rozwiązań trzeba ręcznie zsynchronizować je z innych projektów.
  * Łatwe generowanie pakietu NuGet zużycia.
  * Umożliwia pisanie kodu dla określonej wersji środowiska .NET Framework w bibliotekach przy użyciu dyrektywy kompilatora.

  *Nieobsługiwane scenariusze:*
  * Wymaga deweloperom umożliwia otwieranie istniejących projektów Visual Studio 2017 r. Do obsługi starszych wersji programu Visual Studio, [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.

* <a name="support-vs"></a>[**Zachowaj oddzielne istniejących i nowych projektów .NET Core**][option-csproj-folder]

  *Co to jest dobre dla:*
  * Kontynuowanie obsługuje programowanie w istniejących projektów bez konieczności aktualizacji dla deweloperów/współautorzy, którzy nie może mieć Visual Studio 2017 r.
  * Zmniejszenie możliwość tworzenia nowych usterek w istniejących projektów, ponieważ postęp dokonany w kodzie jest wymagany w tych projektach.

## <a name="example"></a>Przykład

Należy wziąć pod uwagę poniższe repozytorium:

![Istniejący projekt][example-initial-project]

[**Kod źródłowy**][example-initial-project-code]

Poniżej przedstawiono kilka sposobów, aby dodać obsługę tego repozytorium, w zależności od ograniczeń i złożoność istniejące projekty dla platformy .NET Core.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Zamień istniejące projekty docelowe multi projekt .NET Core

Reorganizacja repozytorium, tak aby każda istniejących  *\*.csproj* pliki są usuwane i na jednym  *\*.csproj* tworzony jest plik, który jest przeznaczony dla wielu platform. Jest to doskonałe rozwiązanie, ponieważ jeden projekt jest w stanie kompilacji dla różnych platform. Ma również uprawnienia do obsługi opcji różnych kompilacji i zależności na platforma docelowa.

![Utwórz csproj, przeznaczonego dla wielu struktur][example-csproj]

[**Kod źródłowy**][example-csproj-code]

Zmiany, należy pamiętać, są następujące:
* Zastąpienie *packages.config* i  *\*.csproj* o nowe [.NET Core  *\*.csproj* ] [ example-csproj-netcore]. Pakiety NuGet są określane za pomocą `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachowaj istniejące projekty i tworzenie projektu platformy .NET Core

W przypadku istniejących projektów, które odnoszą się do starszej ramy można pozostawić bez zmian te projekty i przyszłych platform docelowych przy użyciu projektu platformy .NET Core.

![Projekt .NET core z istniejącego projektu w innym folderze][example-csproj-different-folder]

[**Kod źródłowy**][example-csproj-different-code]

Zmiany, należy pamiętać, są następujące:
* Oprogramowanie .NET Core i istniejące projekty są przechowywane w oddzielnych folderach.
    * Utrzymywanie projekty w oddzielnych folderach pozwala uniknąć wymuszania posiadania programu Visual Studio 2017 r. Można utworzyć oddzielnym rozwiązaniu otwartym tylko starych projektów.

## <a name="see-also"></a>Zobacz też

Zobacz [.NET Core eksportowanie dokumentacji] [ porting-doc] Aby uzyskać więcej pomocy na temat migracji do platformy .NET Core.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Istniejący projekt"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Utwórz csproj, przeznaczonego dla wielu struktur"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Oprogramowanie .NET core projekt z istniejących PCL w innym folderze"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
