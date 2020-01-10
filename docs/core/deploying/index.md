---
title: Wdrażanie aplikacji .NET Core
description: Dowiedz się więcej na temat sposobów wdrażania aplikacji .NET Core.
ms.date: 12/03/2018
ms.openlocfilehash: 41c5285f2a9ddf38e4be7326bd5cba1c58370fe7
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740808"
---
# <a name="net-core-application-deployment"></a>Wdrażanie aplikacji .NET Core

Można utworzyć trzy typy wdrożeń dla aplikacji platformy .NET Core:

- Wdrożenie zależne od platformy. Jak nazywa się, wdrożenie zależne od platformy (FDD) zależy od obecności udostępnionej systemowej wersji platformy .NET Core w systemie docelowym. Ponieważ platforma .NET Core już istnieje, aplikacja jest również przenośna między instalacjami programu .NET Core. Aplikacja zawiera tylko własny kod i wszystkie zależności innych firm, które znajdują się poza bibliotekami programu .NET Core. FDDs zawierają pliki *dll* , które można uruchomić za pomocą [Narzędzia dotnet](../tools/dotnet.md) z wiersza polecenia. Na przykład `dotnet app.dll` uruchamia aplikację o nazwie `app`.

- Wdrażanie samodzielne. W przeciwieństwie do FDD, wdrożenie samodzielne (SCD) nie polega na obecności składników udostępnionych w systemie docelowym. Wszystkie składniki, w tym biblioteki .NET Core i środowisko uruchomieniowe platformy .NET Core, są dołączone do aplikacji i są odizolowane od innych aplikacji platformy .NET Core. SCDs obejmują plik wykonywalny (na przykład *App. exe* na platformach systemu Windows dla aplikacji o nazwie `app`), która jest nazwą o zmienionej nazwie hosta .NET Core i plikiem *dll* (na przykład *App. dll*), która jest rzeczywistą aplikacją.

- Pliki wykonywalne zależne od struktury. Tworzy plik wykonywalny, który działa na platformie docelowej. Podobnie jak w przypadku FDDs, pliki wykonywalne zależne od struktury (całego) są specyficzne dla platformy i nie są samodzielne. Te wdrożenia nadal polegają na obecności udostępnionej wersji systemu .NET Core do uruchomienia. W przeciwieństwie do SCD, aplikacja zawiera tylko kod i wszystkie zależności innych firm, które są poza bibliotekami programu .NET Core. FDEs tworzy plik wykonywalny, który działa na platformie docelowej.

## <a name="framework-dependent-deployments-fdd"></a>Wdrożenia zależne od platformy (FDD)

W przypadku FDD należy wdrożyć tylko aplikacje i zależności innych firm. Twoja aplikacja będzie używać wersji platformy .NET Core, która jest obecna w systemie docelowym. Jest to domyślny model wdrażania dla programu .NET Core i ASP.NET Core aplikacji przeznaczonych dla platformy .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Dlaczego warto utworzyć wdrożenie zależne od platformy?

Wdrożenie FDD ma wiele zalet:

- Nie trzeba definiować docelowych systemów operacyjnych, z których aplikacja platformy .NET Core będzie działać z wyprzedzeniem. Ponieważ .NET Core używa typowego formatu pliku PE dla plików wykonywalnych i bibliotek niezależnie od systemu operacyjnego, program .NET Core może wykonać swoją aplikację niezależnie od bazowego systemu operacyjnego. Aby uzyskać więcej informacji na temat formatu pliku PE, zobacz [Format pliku zestawu .NET](../../standard/assembly/file-format.md).

- Rozmiar pakietu wdrożeniowego jest mały. Wdrażasz tylko aplikację i jej zależności, a nie same platformy .NET Core.

- O ile nie zostanie zastąpiony, FDDs będzie używać najnowszego środowiska uruchomieniowego zainstalowanego w systemie docelowym. Dzięki temu aplikacja może używać najnowszej wersji poprawki środowiska uruchomieniowego platformy .NET Core. 

- Wiele aplikacji korzysta z tej samej instalacji programu .NET Core, co zmniejsza użycie miejsca na dysku i pamięci w systemach hosta.

Istnieją również pewne wady:

- Aplikacja może działać tylko wtedy, gdy wersja platformy .NET Core aplikacji [lub nowsza wersja](../versions/selection.md#framework-dependent-apps-roll-forward)jest już zainstalowana w systemie hosta.

- Istnieje możliwość zmiany środowiska uruchomieniowego i bibliotek platformy .NET Core bez wiedzy w przyszłych wydaniach. W rzadkich przypadkach może to zmienić zachowanie aplikacji.

## <a name="self-contained-deployments-scd"></a>Wdrożenia samodzielne (SCD)

W przypadku wdrożenia z dowolnego siebie należy wdrożyć aplikację i wszystkie wymagane zależności innych firm wraz z wersją platformy .NET Core, która została użyta do skompilowania aplikacji. Tworzenie SCD nie obejmuje [natywnych zależności programu .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na różnych platformach, dlatego muszą one być obecne przed uruchomieniem aplikacji. Aby uzyskać więcej informacji na temat powiązania wersji w środowisku uruchomieniowym, zapoznaj się z artykułem na temat [powiązania wersji w programie .NET Core](../versions/selection.md).

Począwszy od zestawu SDK programu .NET Core 2,1 (wersja 2.1.300), platforma ASP.NET Core obsługuje funkcję *wycofywania wersji poprawek*. W przypadku tworzenia własnego wdrożenia narzędzia platformy .NET Core automatycznie uwzględniają najnowsze środowisko uruchomieniowe programu .NET Core, do którego odwołuje się aplikacja. (Najnowsza obsługa środowiska uruchomieniowego obejmuje poprawki zabezpieczeń i inne poprawki błędów). Obsługiwane środowisko uruchomieniowe nie musi być obecne w systemie kompilacji; jest ona pobierana automatycznie z NuGet.org. Aby uzyskać więcej informacji, w tym instrukcje dotyczące sposobu rezygnacji z wersji poprawki do przodu, zobacz [samodzielne wdrożenie środowiska uruchomieniowego wdrożenia](runtime-patch-selection.md).

Wdrożenia FDD i SCD korzystają z oddzielnych plików wykonywalnych hosta, więc można podpisać plik wykonywalny hosta dla SCD za pomocą podpisu wydawcy.

### <a name="why-deploy-a-self-contained-deployment"></a>Dlaczego warto wdrożyć wdrożenie samodzielne?

Wdrożenie samodzielnego wdrożenia ma dwie główne zalety:

- Masz wyłączną kontrolę wersji platformy .NET Core wdrożonej wraz z Twoją aplikacją. Platforma .NET Core może być serwisowana tylko przez użytkownika.

- Możesz mieć pewność, że system docelowy może uruchomić aplikację .NET Core, ponieważ udostępniasz wersję programu .NET Core, na której będzie działać.

Ma również różne wady:

- Ponieważ platforma .NET Core jest dołączona do pakietu wdrożeniowego, należy wybrać Platformy docelowe, dla których skompilowano pakiety wdrożeniowe.

- Rozmiar pakietu wdrożeniowego jest stosunkowo duży, ponieważ trzeba uwzględnić platformę .NET Core oraz swoją aplikację i jej zależności.

  Począwszy od platformy .NET Core 2,0, można zmniejszyć rozmiar wdrożenia w systemach Linux o około 28 MB przy użyciu [*trybu niezmiennej globalizacji*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)platformy .NET Core. Zwykle platforma .NET Core w systemie Linux opiera się na [bibliotekach ICU](http://icu-project.org) na potrzeby obsługi globalizacji. W trybie niezmiennym biblioteki nie są uwzględniane we wdrożeniu, a wszystkie kultury zachowują się jak [Niezmienna kultura](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- Wdrożenie wielu samodzielnych aplikacji platformy .NET Core w systemie może zużywać znaczną ilość miejsca na dysku, ponieważ każda aplikacja duplikuje pliki .NET Core.

## <a name="framework-dependent-executables-fde"></a>Pliki wykonywalne zależne od platformy (całego)

Począwszy od platformy .NET Core 2,2, możesz wdrożyć aplikację jako całego, a także wszystkie wymagane zależności innych firm. Twoja aplikacja będzie używać wersji programu .NET Core zainstalowanej w systemie docelowym.

### <a name="why-deploy-a-framework-dependent-executable"></a>Dlaczego należy wdrożyć plik wykonywalny zależny od platformy?

Wdrożenie całego ma wiele zalet:

- Rozmiar pakietu wdrożeniowego jest mały. Wdrażasz tylko aplikację i jej zależności, a nie same platformy .NET Core.

- Wiele aplikacji korzysta z tej samej instalacji programu .NET Core, co zmniejsza użycie miejsca na dysku i pamięci w systemach hosta.

- Aplikację można uruchomić, wywołując opublikowany plik wykonywalny bez wywoływania bezpośrednio narzędzia `dotnet`.

Istnieją również pewne wady:

- Aplikacja może działać tylko wtedy, gdy wersja platformy .NET Core aplikacji [lub nowsza wersja](../versions/selection.md#framework-dependent-apps-roll-forward)jest już zainstalowana w systemie hosta.

- Istnieje możliwość zmiany środowiska uruchomieniowego i bibliotek platformy .NET Core bez wiedzy w przyszłych wydaniach. W rzadkich przypadkach może to zmienić zachowanie aplikacji.

- Musisz opublikować aplikację dla każdej platformy docelowej.

## <a name="step-by-step-examples"></a>Przykłady krok po kroku

Aby zapoznać się z przykładami krok po kroku wdrażania aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia, zobacz [wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia](deploy-with-cli.md). Aby zapoznać się z przykładami krok po kroku wdrażania aplikacji .NET Core za pomocą programu Visual Studio, zobacz [wdrażanie aplikacji .NET Core za pomocą programu Visual Studio](deploy-with-vs.md). 

## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia](deploy-with-cli.md)
- [Wdrażanie aplikacji .NET Core za pomocą programu Visual Studio](deploy-with-vs.md)
- [Pakiety, metapakiety i struktury](../packages.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)](../rid-catalog.md)
