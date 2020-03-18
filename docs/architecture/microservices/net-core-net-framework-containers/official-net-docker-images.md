---
title: Oficjalne obrazy Docker w programie .NET
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Oficjalne obrazy platformy Docker .NET
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501876"
---
# <a name="official-net-docker-images"></a>Oficjalne obrazy Docker w programie .NET

Oficjalne obrazy platformy Docker .NET są obrazami platformy Docker utworzonymi i zoptymalizowanymi przez firmę Microsoft. Są one publicznie dostępne w repozytoriach firmy Microsoft w centrum [docker hub](https://hub.docker.com/u/microsoft/). Każde repozytorium może zawierać wiele obrazów, w zależności od wersji .NET, i w zależności od systemu operacyjnego i wersji (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core itp.).

Od .NET Core 2.1 wszystkie obrazy .NET Core, w tym dla ASP.NET Core, są dostępne w <https://hub.docker.com/_/microsoft-dotnet-core/>centrum docker hub w repozytorium obrazów .NET Core: .

Od maja 2018 r. obrazy firmy Microsoft są [syndykowane w rejestrze kontenerów firmy Microsoft](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/). Oficjalny katalog jest nadal dostępny tylko w centrum docker hub, a tam znajdziesz zaktualizowany adres, aby ściągnąć obraz.

Większość repozytoriów obrazów zapewnia rozbudowane tagowanie, które ułatwia wybór nie tylko określonej wersji framework, ale także wybór systemu operacyjnego (dystrybucja systemu Linux lub wersja systemu Windows).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Optymalizacje obrazów .NET Core i Docker dla rozwoju i produkcji

Podczas tworzenia obrazów platformy Docker dla deweloperów firma Microsoft skupiła się na następujących głównych scenariuszach:

- Obrazy używane do *tworzenia* i tworzenia aplikacji .NET Core.

- Obrazy używane do *uruchamiania* aplikacji .NET Core.

Dlaczego wiele obrazów? Podczas tworzenia, tworzenia i uruchamiania aplikacji konteneryzowanych, zwykle mają różne priorytety. Udostępniając różne obrazy dla tych oddzielnych zadań, firma Microsoft pomaga zoptymalizować oddzielne procesy tworzenia, tworzenia i wdrażania aplikacji.

### <a name="during-development-and-build"></a>Podczas rozwoju i budowania

Podczas tworzenia, co jest ważne jest, jak szybko można iterować zmiany i możliwość debugowania zmian. Rozmiar obrazu nie jest tak ważne, jak możliwość wprowadzania zmian w kodzie i szybko zobaczyć zmiany. Niektóre narzędzia i "kontenery build-agent", użyj obrazu programu .NET Core *(mcr.microsoft.com/dotnet/core/sdk:3.1)* podczas procesu tworzenia i kompilacji. Podczas tworzenia wewnątrz kontenera platformy Docker, ważne aspekty są elementy, które są potrzebne do skompilowania aplikacji. Obejmuje to kompilator i wszelkie inne zależności .NET.

Dlaczego ten typ obrazu kompilacji jest ważny? Nie należy wdrażać ten obraz w środowisku produkcyjnym. Zamiast tego jest to obraz, który służy do tworzenia zawartości, które można umieścić w obrazie produkcyjnym. Ten obraz będzie używany w środowisku ciągłej integracji (CI) lub środowiska kompilacji podczas korzystania z platformy Docker kompilacje wielostopniowe.

### <a name="in-production"></a>W produkcji

Co jest ważne w środowisku produkcyjnym jest jak szybko można wdrożyć i uruchomić kontenery na podstawie obrazu produkcyjnego .NET Core. W związku z tym obraz tylko w czasie wykonywania na podstawie *mcr.microsoft.com/dotnet/core/aspnet:3.1* jest mały, dzięki czemu można szybko podróżować po sieci z rejestru platformy Docker do hostów platformy Docker. Zawartość jest gotowa do uruchomienia, umożliwiając najszybszy czas od uruchomienia kontenera do przetwarzania wyników. W modelu platformy Docker nie ma\# potrzeby kompilacji z kodu C, jak jest po uruchomieniu kompilacji dotnet lub dotnet publikowania podczas korzystania z kontenera kompilacji.

W tym zoptymalizowanym obrazie można umieścić tylko pliki binarne i inną zawartość potrzebną do uruchomienia aplikacji. Na przykład zawartość utworzona `dotnet publish` przez zawiera tylko skompilowane pliki binarne .NET, obrazy, .js i .css. Wraz z upływu czasu zostaną wyświetlone obrazy, które zawierają wstępnie wyjmowane (kompilacja z IL do macierzystych, który występuje w czasie wykonywania) pakietów.

Chociaż istnieje wiele wersji obrazów .NET Core i ASP.NET Core, wszystkie one współużytkują jedną lub więcej warstw, w tym warstwę bazową. W związku z tym ilość miejsca na dysku potrzebnedo przechowywania obrazu jest mała; składa się tylko z różnic między obrazem niestandardowym a jego obrazem bazowym. W rezultacie szybko można wyciągnąć obraz z rejestru.

Podczas eksplorowania repozytoriów obrazów .NET w centrum docker hub znajdziesz wiele wersji obrazów sklasyfikowanych lub oznaczonych tagami. Te tagi pomagają zdecydować, którego z nich użyć, w zależności od potrzebnej wersji, takiej jak te w poniższej tabeli:

| Image (Obraz) | Komentarze |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet:**3,1** | ASP.NET Core, z tylko środowiska uruchomieniowego i ASP.NET optymalizacje rdzenia, w systemie Linux i Windows (multi-arch) |
| mcr.microsoft.com/dotnet/core/sdk:**3,1** | .NET Core, z dołączonymi zestawami SDK, w systemach Linux i Windows (multi-arch) |

> [!div class="step-by-step"]
> [Poprzedni](net-container-os-targets.md)
> [następny](../architect-microservice-container-applications/index.md)
