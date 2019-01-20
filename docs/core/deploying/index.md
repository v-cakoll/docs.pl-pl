---
title: Wdrożenie aplikacji programu .NET core
description: Poznaj sposoby wdrażania aplikacji .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 12/03/2018
ms.custom: seodec18
ms.openlocfilehash: bb520d852462b0bc12df46fd178d09da36b7ccfe
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415692"
---
# <a name="net-core-application-deployment"></a>Wdrażanie aplikacji .NET core

Można utworzyć trzy typy wdrożeń dla aplikacji .NET Core:

- Framework-dependent deployment. Jak wskazuje nazwa, zależny od struktury wdrożenia (stacje) zależy od obecności udostępnione całego systemu w wersji programu .NET Core w systemie docelowym. Ponieważ platformy .NET Core jest już obecny, Twoja aplikacja jest również do przenoszenia pomiędzy instalacji programu .NET Core. Aplikacja zawiera tylko własnego kodu i wszelkie zależności innych firm, które znajdują się poza biblioteki .NET Core. Zawiera FDDs *.dll* pliki, które można uruchamiać przy użyciu [narzędzia dotnet](../tools/dotnet.md) z wiersza polecenia. Na przykład `dotnet app.dll` uruchamia aplikację o nazwie `app`.

- Niezależne wdrożenia. W odróżnieniu od Dyskietki niezależna wdrożenia (— SCD) nie jest zależny od obecności składniki współużytkowane w systemie docelowym. Wszystkie składniki, łącznie z biblioteki .NET Core i środowisko uruchomieniowe platformy .NET Core, są dołączone do aplikacji i odizolowane od innych aplikacji .NET Core. SCDs obejmują plik wykonywalny (takie jak *app.exe* na platformach Windows, dla aplikacji o nazwie `app`), czyli wersji zmieniono nazwę hosta, specyficzne dla platformy .NET Core, a *.dll* pliku (np. *app.dll*), który jest rzeczywista aplikacja.

- Pliki wykonywalne zależny od struktury. Tworzy plik wykonywalny, który działa na platformie docelowej. Podobnie jak FDDs, zależny od struktury plików wykonywalnych (FDE) są specyficzne dla platformy i nie są niezależne. Te wdrożenia nadal zależy od obecności udostępniona wersja systemowe programu .NET Core do uruchomienia. W odróżnieniu od — SCD aplikacji zawiera tylko kod i wszelkie zależności innych firm, które znajdują się poza biblioteki .NET Core. FDEs generuje plik wykonywalny, który działa na platformie docelowej.

## <a name="framework-dependent-deployments-fdd"></a>Zależny od struktury wdrożeń (stacje)

STACJE wdrożysz swojej aplikacji i zależności innych firm. Twoja aplikacja będzie używać wersji programu .NET Core, który znajduje się w systemie docelowym. Jest to domyślny model wdrażania dla aplikacji platformy .NET Core i ASP.NET Core, przeznaczonych dla platformy .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Dlaczego warto tworzyć wdrożenia zależny od struktury?

Wdrażanie z stacje ma szereg zalet:

- Nie trzeba zdefiniować systemów operacyjnych, korzystających z aplikacji .NET Core będą z wyprzedzeniem. Ponieważ platformy .NET Core używa wspólny format plików PE w przypadku plików wykonywalnych i bibliotek, niezależnie od systemu operacyjnego, platformy .NET Core można wykonać aplikacji niezależnie od zasadniczego systemu operacyjnego. Aby uzyskać więcej informacji o formacie pliku PE, zobacz [Format pliku zestawu .NET](../../standard/assembly-format.md).

- Rozmiar pakietu wdrażania jest mały. Można wdrażać tylko w aplikacji oraz jego zależności, a nie .NET Core sam.

- O ile nie została zastąpiona, FDDs użyje najnowszej obsługiwanych środowiska uruchomieniowego zainstalowanego w systemie docelowym. Dzięki temu aplikacja korzystała poprawionego najnowszej wersji środowiska uruchomieniowego .NET Core. 

- Wiele aplikacji używać tego samego instalacji platformy .NET Core, co zmniejsza zarówno dysku miejsca oraz użycia pamięci w systemach hosta.

Dostępne są również kilka wady:

- Aplikację można uruchomić tylko wtedy, gdy wersję platformy .NET Core Twojej aplikacji jest przeznaczony dla [lub nowsza wersja](../versions/selection.md#framework-dependent-apps-roll-forward), jest już zainstalowany w systemie hosta.

- Jest to możliwe, środowisko uruchomieniowe programu .NET Core i bibliotek, które można zmienić bez wiedzy użytkownika w przyszłych wersjach. W rzadkich przypadkach może to spowodować zmianę zachowania aplikacji.

## <a name="self-contained-deployments-scd"></a>Niezależne wdrożenia (— SCD)

Niezależne wdrożenia możesz wdrożyć aplikację i wszystkie wymagane zależności innych firm, wraz z wersją programu .NET Core, używanym do tworzenia aplikacji. Tworzenie — SCD nie obejmuje [natywnych zależności platformy .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na różnych platformach, więc te musi występować przed uruchomieniem aplikacji. Aby uzyskać więcej informacji, wiązanie wersji w czasie wykonywania, zobacz artykuł w [wiązanie wersji w programie .NET Core](../versions/selection.md).

Począwszy od zestawu SDK NET Core 2.1 (wersja 2.1.300), .NET Core obsługuje *poprawki wersji przenoszenia do przodu*. Podczas tworzenia wdrożenia niezależna narzędzia .NET Core automatycznie uwzględnia najnowszych obsługiwanych środowiska uruchomieniowego wersji platformy .NET Core, Twoje cele aplikacji. (Najnowsza wersja obsługiwanych środowiska uruchomieniowego w tym poprawki zabezpieczeń i inne poprawki.) Obsługiwane środowiska uruchomieniowego musi być obecny w systemie kompilacji; jest ona pobierana automatycznie z repozytorium NuGet.org. Aby uzyskać więcej informacji, w tym instrukcje dotyczące sposobu zrezygnować z poprawki wersji przenoszenia do przodu, zobacz [niezależna wdrażania środowiska uruchomieniowego przenoszenia do przodu](runtime-patch-selection.md).

Wdrożenia z stacje i — SCD za pomocą hosta oddzielnych plików wykonywalnych, dzięki czemu możesz zarejestrować wykonywalnego hosta — SCD do podpisu wydawcy.

### <a name="why-deploy-a-self-contained-deployment"></a>Dlaczego warto wdrożyć niezależna wdrożenia?

Niezależna wdrożenie ma dwie główne korzyści:

- Masz wyłączną kontrolę wersji platformy .NET Core, który jest wdrożony z aplikacją. .NET core może być obsługiwany tylko przez użytkownika.

- Możesz mieć pewność, system docelowy można uruchomić aplikację .NET Core, ponieważ udostępniasz wersję platformy .NET Core, która zostanie uruchomiona na.

Ponadto wprowadzono szereg wady:

- Ponieważ platformy .NET Core jest uwzględniony w pakiecie wdrożenia, należy wybrać platformy docelowe, dla których można tworzyć pakiety wdrożeniowe z wyprzedzeniem.

- Rozmiar pakietu wdrażania jest stosunkowo dużych, ponieważ należy dołączyć platformy .NET Core oraz aplikacji i jej zależności innych firm.

  Począwszy od programu .NET Core 2.0, można zmniejszyć rozmiaru wdrożenia przez około 28 MB w systemach Linux przy użyciu platformy .NET Core [ *globalizacji niezmiennej tryb*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md). Zazwyczaj, .NET Core w systemie Linux opiera się na [bibliotek ICU](https://github.com/dotnet/docs/issues/http%22//icu-project.org) obsługi globalizacji. W trybie niezmiennej bibliotek nie są dołączone do wdrożenia i wszystkich kultur zachowują się jak [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- Wdrażanie wielu samodzielne aplikacje platformy .NET Core w systemie może zużywać znacznej ilości miejsca na dysku, od każdej aplikacji duplikatów plików .NET Core.

## <a name="framework-dependent-executables-fde"></a>Zależny od struktury plików wykonywalnych (FDE)

Począwszy od platformy .NET Core 2.2, można wdrożyć aplikację jako FDE oraz wszelkie wymagane zależności innych firm. Twoja aplikacja będzie używać wersji programu .NET Core, który jest zainstalowany w systemie docelowym.

### <a name="why-deploy-a-framework-dependent-executable"></a>Dlaczego warto wdrożyć zależny od struktury pliku wykonywalnego?

Wdrażanie FDE ma szereg zalet:

- Rozmiar pakietu wdrażania jest mały. Można wdrażać tylko w aplikacji oraz jego zależności, a nie .NET Core sam.

- Wiele aplikacji używać tego samego instalacji platformy .NET Core, co zmniejsza zarówno dysku miejsca oraz użycia pamięci w systemach hosta.

- Aplikację można uruchomić, wywołując opublikowanego pliku wykonywalnego bez wywoływania `dotnet` narzędzie bezpośrednio.

Dostępne są również kilka wady:

- Aplikację można uruchomić tylko wtedy, gdy wersję platformy .NET Core Twojej aplikacji jest przeznaczony dla [lub nowsza wersja](../versions/selection.md#framework-dependent-apps-roll-forward), jest już zainstalowany w systemie hosta.

- Jest to możliwe, środowisko uruchomieniowe programu .NET Core i bibliotek, które można zmienić bez wiedzy użytkownika w przyszłych wersjach. W rzadkich przypadkach może to spowodować zmianę zachowania aplikacji.

- Należy opublikować aplikację dla każdej platformy docelowej.

## <a name="step-by-step-examples"></a>Przykłady krok po kroku

Instrukcje krok po kroku wdrażania aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia, zobacz [wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia](deploy-with-cli.md). Instrukcje krok po kroku wdrażania aplikacji .NET Core za pomocą programu Visual Studio, zobacz [wdrażanie aplikacji .NET Core z programem Visual Studio](deploy-with-vs.md). 

## <a name="see-also"></a>Zobacz także

* [Wdrażanie aplikacji programu .NET Core za pomocą narzędzi interfejsu wiersza polecenia](deploy-with-cli.md)
* [Wdrażanie aplikacji programu .NET Core z programem Visual Studio](deploy-with-vs.md)
* [Pakiety, metapakiety i struktury](../packages.md)
* [Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
