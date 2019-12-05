---
title: Organizuj projekty dla .NET Framework i .NET Core
description: Pomoc dla właścicieli projektu, którzy chcą kompilować rozwiązanie względem .NET Framework i .NET Core obok siebie.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 789f50ffb61b80f590a24bc45693df895b3424f7
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801927"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Organizuj projekt, aby obsługiwał zarówno .NET Framework, jak i .NET Core

Dowiedz się, jak utworzyć rozwiązanie, które kompiluje zarówno .NET Framework, jak i .NET Core. Zobacz kilka opcji, aby zorganizować projekty w celu ułatwienia osiągnięcia tego celu. Poniżej przedstawiono kilka typowych scenariuszy, które należy wziąć pod uwagę w przypadku podejmowania decyzji o sposobie konfigurowania układu projektu przy użyciu programu .NET Core. Lista może nie obejmować wszystkiego, czego potrzebujesz; ustalanie priorytetów w zależności od potrzeb projektu.

- [**Połącz istniejące projekty i projekty .NET Core w pojedyncze projekty**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Co to jest dobre dla:*
  - Uproszczenie procesu kompilacji przez skompilowanie pojedynczego projektu, a nie kompilowanie wielu projektów, każdy przeznaczony dla innej wersji .NET Framework lub platformy.
  - Uproszczenie zarządzania plikami źródłowymi dla projektów wielowymiarowych, ponieważ należy zarządzać pojedynczym plikiem projektu. W przypadku dodawania/usuwania plików źródłowych alternatywa wymaga ręcznej synchronizacji z innymi projektami.
  - Łatwe generowanie pakietu NuGet do użycia.
  - Umożliwia pisanie kodu dla konkretnej wersji .NET Framework w bibliotekach za pomocą dyrektyw kompilatora.

  *Nieobsługiwane scenariusze:*
  - Aby otworzyć istniejące projekty, deweloperzy muszą używać programu Visual Studio 2017 lub nowszej wersji. Aby można było obsługiwać starsze wersje programu Visual Studio, [zachowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.

- <a name="support-vs"></a>[**Przechowuj istniejące projekty i nowe projekty .NET Core**](#keep-existing-projects-and-create-a-net-core-project)

  *Co to jest dobre dla:*
  - Obsługa opracowywania istniejących projektów dla deweloperów i współautorów, którzy nie mają programu Visual Studio w wersji 2017 lub nowszej.
  - Zmniejszenie możliwości tworzenia nowych usterek w istniejących projektach, ponieważ w tych projektach nie są wymagane żadne zmiany w kodzie.

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

Zmiany w notatce:

- Środowisko .NET Core i istniejące projekty są przechowywane w oddzielnych folderach.
  - Utrzymywanie projektów w oddzielnych folderach pozwala uniknąć wymuszania programu Visual Studio w wersji 2017 lub nowszej. Można utworzyć oddzielne rozwiązanie, które otwiera tylko stare projekty.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja dotycząca portów .NET Core](index.md)
