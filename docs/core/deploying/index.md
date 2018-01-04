---
title: "Wdrażanie aplikacji .NET core"
description: "Wdrażanie aplikacji .NET Core."
keywords: "Wdrożenie .NET Core .NET i .NET core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
ms.workload: dotnetcore
ms.openlocfilehash: 87a70ac246e37c646f9be578a03dda7037cfdd2d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-application-deployment"></a>Wdrażanie aplikacji .NET core

Można tworzyć dwa typy wdrożeń dla aplikacji .NET Core:

- Zależne od Framework wdrożenia. Jak wskazuje nazwę, zależne od framework wdrożenia (stacje) zależy od obecności udostępnionego systemowe wersji platformy .NET Core w systemie docelowym. Ponieważ .NET Core jest już obecny, aplikacji jest również przenosić między instalacji platformy .NET Core. Aplikacja zawiera tylko własnego kodu i wszelkie zależności innych firm, które znajdują się poza bibliotek .NET Core. Zawiera FDDs *.dll* pliki, które można uruchomić przy użyciu [narzędzie dotnet](../tools/dotnet.md) z wiersza polecenia. Na przykład `dotnet app.dll` działa aplikacja o nazwie `app`.

- Samodzielne wdrożenia. W odróżnieniu od Dyskietki niezależne wdrożenia (SCD) nie zależą od obecności współużytkowanych składników w systemie docelowym. Wszystkie składniki, w tym zarówno do bibliotek .NET Core i środowiska uruchomieniowego .NET Core, są dołączone do aplikacji i odizolowana od innych aplikacji .NET Core. SCDs obejmują plik wykonywalny (takich jak *app.exe* na platformach systemu Windows dla aplikacji o nazwie `app`), zmieniono nazwę wersji specyficzne dla platformy .NET Core hosta, a *.dll* plików (takich jak *app.dll*), która jest rzeczywista aplikacji.

## <a name="framework-dependent-deployments-fdd"></a>Zależne od Framework wdrożeń (stacje)

STACJE wdrożeniem tylko aplikacji i zależności innych firm. Nie trzeba wdrażać .NET Core, ponieważ Twoja aplikacja będzie używać wersji programu .NET Core, która występuje na komputerze docelowym. Jest to domyślny model wdrażania dla aplikacji .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Dlaczego warto utworzyć wdrożenia framework zależnych?

Wdrażanie Dyskietki ma następujące korzyści:

- Nie trzeba definiować systemów operacyjnych, które aplikacji .NET Core będą działać w wyprzedzeniem. Ponieważ .NET Core używa formacie pliku PE wspólne dla obiektów wykonywalnych i bibliotek niezależnie od systemu operacyjnego, platformy .NET Core można wykonać aplikacji niezależnie od systemu operacyjnego. Aby uzyskać więcej informacji o formacie pliku PE, zobacz [Format pliku zestawu .NET](../../standard/assembly-format.md).

- Rozmiar pakietu wdrażania jest mała. Można wdrażać tylko w aplikacji i jej zależności nie .NET Core samej siebie.

- Wiele aplikacji używać tej samej instalacji .NET Core, co zmniejsza zarówno miejsca i pamięć użycia dysku w systemach hosta.

Dostępne są również kilka wady:

- Aplikację można uruchomić tylko wtedy, gdy jest to wersja platformy .NET Core, które są przeznaczone lub nowszy, jest już zainstalowana w systemie hosta.

- Istnieje możliwość środowiska uruchomieniowego .NET Core i biblioteki można zmienić bez wiedzy użytkownika w przyszłych wersjach. W rzadkich przypadkach może to spowodować zmianę zachowania aplikacji.

## <a name="self-contained-deployments-scd"></a>Samodzielne wdrożeń (SCD)

Niezależne wdrożenia możesz wdrożyć aplikację i wszystkie wymagane zależności innych firm oraz wersji platformy .NET Core, który był używany podczas kompilowania aplikacji. Tworzenie SCD nie zawiera [natywnego zależności programu .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) na różnych platformach, więc te musi występować przed uruchomieniem aplikacji.

Wdrożenia Dyskietki i SCD Użyj hosta oddzielne pliki wykonywalne, więc możesz utworzyć pliku wykonywalnego hosta SCD w podpisie wydawcy.

### <a name="why-deploy-a-self-contained-deployment"></a>Dlaczego wdrożenia niezależne?

Wdrażanie niezależne wdrożenia ma dwie główne zalety:

- Masz wyłączną kontrolę wersji platformy .NET Core, który jest wdrażany z aplikacją. Oprogramowanie .NET core może być obsługiwany tylko przez użytkownika.

- Można mieć pewność, system docelowy można uruchomić aplikacji .NET Core, ponieważ jest zapewnienie wersji programu .NET Core, który będzie uruchamiany na.

Ma on również szereg wady:

- Ponieważ .NET Core znajduje się w pakiecie wdrożenia, musisz wybrać platformy docelowe, dla których tworzenia pakietów wdrożeniowych z wyprzedzeniem.

- Rozmiar pakietu wdrażania jest stosunkowo dużej, ponieważ powinien obejmować oprogramowanie .NET Core, a także aplikacji i jej zależności innych firm.

- Wdrażania wielu niezależne aplikacji .NET Core do systemu, jaką może wykorzystać znacznej ilości miejsca na dysku, od każdej aplikacji duplikaty plików .NET Core.

## <a name="step-by-step-examples"></a>Przykłady krok po kroku

Przykłady krok po kroku wdrażania aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia, zobacz [wdrażanie aplikacji programu .NET Core przy użyciu narzędzi interfejsu wiersza polecenia](deploy-with-cli.md). Przykłady krok po kroku wdrażania aplikacji .NET Core za pomocą programu Visual Studio, zobacz [wdrażanie aplikacji programu .NET Core z programem Visual Studio](deploy-with-vs.md). Każdego tematu zawiera przykłady następujących wdrożeń:

- Zależne od Framework wdrożenia
- Wdrożenie Framework zależne zależności innych firm
- Samodzielne wdrożenia
- Samodzielne wdrożenia zależności innych firm

# <a name="see-also"></a>Zobacz także

[Wdrażanie aplikacji .NET Core za pomocą narzędzi interfejsu wiersza polecenia](deploy-with-cli.md)   
[Wdrażanie aplikacji programu .NET Core z programem Visual Studio](deploy-with-vs.md)   
[Pakiety, Metapackages i platform](../packages.md)   
[Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
