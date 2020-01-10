---
title: Organizuj projekty dla .NET Framework i .NET Core
description: Pomoc dla właścicieli projektu, którzy chcą kompilować rozwiązanie względem .NET Framework i .NET Core obok siebie.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777333"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Organizuj projekt, aby obsługiwał zarówno .NET Framework, jak i .NET Core

Można utworzyć rozwiązanie, które kompiluje zarówno .NET Framework, jak i .NET Core obok siebie. W tym artykule opisano kilka opcji organizacji projektu, które ułatwiają osiągnięcie tego celu. Poniżej przedstawiono kilka typowych scenariuszy, które należy wziąć pod uwagę podczas konfigurowania układu projektu przy użyciu platformy .NET Core. Lista może nie obejmować wszystkiego, czego potrzebujesz; ustalanie priorytetów w zależności od potrzeb projektu.

- [**Połącz istniejące projekty i projekty .NET Core w pojedyncze projekty**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Co to jest dobre dla:*
  - Upraszcza proces kompilacji, kompilując pojedynczy projekt, a nie wiele projektów, które są przeznaczone dla różnych wersji .NET Framework lub platform.
  - Upraszcza zarządzanie plikami źródłowymi dla projektów wielowymiarowych, ponieważ należy zarządzać pojedynczym plikiem projektu. W przypadku dodawania lub usuwania plików źródłowych alternatywa wymaga ręcznej synchronizacji z innymi projektami.
  - Łatwo Generuj pakiet NuGet do użycia.
  - Umożliwia pisanie kodu dla konkretnej wersji .NET Framework w bibliotekach za pomocą dyrektyw kompilatora.

  *Nieobsługiwane scenariusze:*
  - Aby otworzyć istniejące projekty, deweloperzy muszą używać programu Visual Studio 2017 lub nowszej wersji. Aby można było obsługiwać starsze wersje programu Visual Studio, [zachowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.

- <a name="support-vs"></a>[**Przechowuj istniejące projekty i nowe projekty .NET Core**](#keep-existing-projects-and-create-a-net-core-project)

  *Co to jest dobre dla:*
  - Obsługuje programowanie w istniejących projektach dla deweloperów i współpracowników, którzy nie mają programu Visual Studio w wersji 2017 lub nowszej.
  - Zmniejsza możliwość tworzenia nowych usterek w istniejących projektach, ponieważ w tych projektach nie są wymagane żadne zmiany w kodzie.

## <a name="example"></a>Przykład

Rozważ następujące repozytorium:

![Istniejący projekt](./media/project-structure/existing-project-structure.png)

[**Kod źródłowy**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

Poniżej opisano kilka sposobów dodawania obsługi platformy .NET Core dla tego repozytorium w zależności od ograniczeń i złożoności istniejących projektów.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Zastąp istniejące projekty z wielowymiarowym projektem platformy .NET Core

Uporządkuj repozytorium, aby wszystkie istniejące pliki *\*. csproj* zostały usunięte, a plik *\*. csproj* zostanie utworzony, który jest przeznaczony dla wielu struktur. Jest to świetna opcja, ponieważ pojedynczy projekt jest w stanie kompilować dla różnych platform. Ma także moc do obsługi różnych opcji kompilacji i zależności dla platformy dostosowanej.

![Utwórz element csproj, który jest przeznaczony dla wielu struktur](./media/project-structure/multi-targeted-project.png)

[**Kod źródłowy**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Zmiany w notatce:

- Zastąpienie elementów *Packages. config* i *\*. csproj* przy użyciu nowego [\*.NET Core *. csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Pakiety NuGet są określone za pomocą `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachowaj istniejące projekty i Utwórz projekt platformy .NET Core

Jeśli istnieją projekty, które są przeznaczone dla starszych platform, możesz pozostawić te projekty jako nienaruszone i użyć projektu .NET Core, aby określić przyszłe struktury.

![Projekt .NET Core z istniejącym projektem w innym folderze](./media/project-structure/separate-projects-same-source.png)

[**Kod źródłowy**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

Środowisko .NET Core i istniejące projekty są przechowywane w oddzielnych folderach. Utrzymywanie projektów w oddzielnych folderach pozwala uniknąć wymuszania programu Visual Studio w wersji 2017 lub nowszej. Można utworzyć oddzielne rozwiązanie, które otwiera tylko stare projekty.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja dotycząca portów .NET Core](index.md)
