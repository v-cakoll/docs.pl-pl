---
title: Organizowanie projektów dla platform .NET Framework i .NET Core
description: Pomoc dla właścicieli projektów, którzy chcą skompilować swoje rozwiązanie względem .NET Framework i .NET Core side-by-side.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777333"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Organizowanie projektu w celu obsługi programu .NET Framework i programu .NET Core

Można utworzyć rozwiązanie, które kompiluje zarówno .NET Framework i .NET Core side-by-side. W tym artykule omówiono kilka opcji organizacji projektu, które pomogą Ci osiągnąć ten cel. Oto kilka typowych scenariuszy, które należy wziąć pod uwagę przy podejmowaniu decyzji, jak skonfigurować układ projektu za pomocą programu .NET Core. Lista może nie obejmować wszystkiego, co chcesz; priorytetowo w zależności od potrzeb projektu.

- [**Łączenie istniejących projektów i projektów .NET Core w pojedyncze projekty**](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  *Co to jest dobre dla:*
  - Upraszcza proces kompilacji przez kompilacji jednego projektu, a nie wiele projektów, które każdy docelowy innej wersji .NET Framework lub platformy.
  - Upraszcza zarządzanie plikami źródłowymi dla projektów wielokierunkowych, ponieważ należy zarządzać pojedynczym plikiem projektu. Podczas dodawania lub usuwania plików źródłowych, alternatywy wymagają ręcznej synchronizacji z innymi projektami.
  - Łatwo wygenerować pakiet NuGet do użycia.
  - Umożliwia pisanie kodu dla określonej wersji .NET Framework w bibliotekach za pomocą dyrektyw kompilatora.

  *Nieobsługiwane scenariusze:*
  - Wymaga od deweloperów użycia programu Visual Studio 2017 lub nowszej wersji do otwierania istniejących projektów. Aby obsługiwać starsze wersje programu Visual Studio, [przechowywanie plików projektu w różnych folderach](#support-vs) jest lepszym rozwiązaniem.

- <a name="support-vs"></a>[**Oddziel istniejące projekty i nowe projekty .NET Core**](#keep-existing-projects-and-create-a-net-core-project)

  *Co to jest dobre dla:*
  - Obsługuje tworzenie istniejących projektów dla deweloperów i współpracowników, którzy mogą nie mieć programu Visual Studio 2017 lub nowszej wersji.
  - Zmniejsza możliwość tworzenia nowych błędów w istniejących projektach, ponieważ w tych projektach nie jest wymagany żaden współczynnik zmian kodu.

## <a name="example"></a>Przykład

Rozważmy repozytorium poniżej:

![Istniejący projekt](./media/project-structure/existing-project-structure.png)

[**Kod źródłowy**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

W poniższym artykule opisano kilka sposobów dodawania obsługi programu .NET Core dla tego repozytorium w zależności od ograniczeń i złożoności istniejących projektów.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Zastępowanie istniejących projektów wielokierunkowym projektem .NET Core

Zreorganizuj repozytorium tak, aby wszystkie istniejące * \*pliki csproj* zostały usunięte i utworzony jest pojedynczy * \*plik csproj,* który jest przeznaczony dla wielu struktur. Jest to świetna opcja, ponieważ pojedynczy projekt jest w stanie skompilować dla różnych struktur. Posiada również możliwość obsługi różnych opcji kompilacji i zależności na ukierunkowane framework.

![Tworzenie csproj, który jest przeznaczony dla wielu struktur](./media/project-structure/multi-targeted-project.png)

[**Kod źródłowy**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

Zmiany w uwagach to:

- Wymiana *packages.config* i * \*.csproj* na nowy [.NET Core * \*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj). Pakiety NuGet są `<PackageReference> ItemGroup`określone za pomocą .

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachowaj istniejące projekty i utwórz projekt .NET Core

Jeśli istnieją projekty, które są przeznaczone dla starszych struktur, można pozostawić te projekty nietknięte i użyć projektu .NET Core do docelowych przyszłych struktur.

![Projekt .NET Core z istniejącym projektem w innym folderze](./media/project-structure/separate-projects-same-source.png)

[**Kod źródłowy**](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

.NET Core i istniejące projekty są przechowywane w oddzielnych folderach. Przechowywanie projektów w oddzielnych folderach pozwala uniknąć zmuszania do programu Visual Studio 2017 lub nowszych wersji. Można utworzyć oddzielne rozwiązanie, które otwiera tylko stare projekty.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja przenoszenia programu .NET Core](index.md)
