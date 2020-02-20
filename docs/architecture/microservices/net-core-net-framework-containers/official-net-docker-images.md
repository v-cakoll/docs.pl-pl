---
title: Oficjalne obrazy Docker w programie .NET
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Oficjalne obrazy platformy Docker .NET
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501876"
---
# <a name="official-net-docker-images"></a>Oficjalne obrazy Docker w programie .NET

Oficjalne obrazy platformy .NET Docker to obrazy platformy Docker utworzone i zoptymalizowane przez firmę Microsoft. Są one publicznie dostępne w repozytoriach firmy Microsoft w usłudze [Docker Hub](https://hub.docker.com/u/microsoft/). Każde repozytorium może zawierać wiele obrazów, w zależności od wersji .NET, a także w zależności od systemu operacyjnego i wersji (Linux Debian, .NET Alpine, Windows nano Server, Windows Server Core itp.).

Od platformy .NET Core 2,1 wszystkie obrazy .NET Core, w tym ASP.NET Core są dostępne w usłudze Docker Hub w repozytorium obrazów programu .NET Core: <https://hub.docker.com/_/microsoft-dotnet-core/>.

Od 2018 maja, [w Container Registry firmy Microsoft są zespolone](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)obrazy firmy Microsoft. Katalog urzędowy nadal jest dostępny tylko w usłudze Docker Hub i znajdziesz zaktualizowany adres, aby ściągnąć obraz.

Większość repozytoriów obrazów zapewnia szeroką tagowanie, która ułatwia wybranie nie tylko określonej wersji platformy, ale również wybranie systemu operacyjnego (dystrybucji systemu Linux lub wersji Windows).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Optymalizacja obrazów .NET Core i Docker na potrzeby programowania i produkcji

Podczas kompilowania obrazów platformy Docker dla deweloperów firma Microsoft koncentruje się na następujących głównych scenariuszach:

- Obrazy używane do *tworzenia* i kompilowania aplikacji platformy .NET Core.

- Obrazy używane do *uruchamiania* aplikacji platformy .NET Core.

Dlaczego wiele obrazów? Podczas opracowywania, kompilowania i uruchamiania aplikacji kontenerowych zwykle są używane różne priorytety. Dostarczając różne obrazy dla tych oddzielnych zadań, firma Microsoft pomaga zoptymalizować poszczególne procesy opracowywania, kompilowania i wdrażania aplikacji.

### <a name="during-development-and-build"></a>Podczas opracowywania i kompilowania

W trakcie opracowywania ważne jest, jak szybko można wykonywać iteracje zmian oraz możliwość debugowania zmian. Rozmiar obrazu nie jest ważny, ponieważ umożliwia wprowadzanie zmian w kodzie i szybkie wyświetlanie zmian. Niektóre narzędzia i "konstruktory agentów kompilacji" wykorzystują program .NET Core Image (*MCR.Microsoft.com/dotnet/Core/SDK:3.1*) podczas tworzenia i kompilowania. Podczas kompilowania wewnątrz kontenera Docker ważne aspekty to elementy, które są potrzebne do skompilowania aplikacji. Obejmuje to kompilator i inne zależności platformy .NET.

Dlaczego ten typ obrazu kompilacji jest ważny? Nie można wdrożyć tego obrazu w środowisku produkcyjnym. Zamiast tego jest to obraz, który służy do tworzenia zawartości umieszczonej na obrazie produkcyjnym. Ten obraz będzie używany w środowisku ciągłej integracji (CI) lub w środowisku kompilacji podczas korzystania z kompilacji wieloetapowych platformy Docker.

### <a name="in-production"></a>W środowisku produkcyjnym

Co jest ważne w środowisku produkcyjnym — szybko można wdrożyć i uruchomić kontenery na podstawie obrazu produkcyjnego platformy .NET Core. W związku z tym obraz tylko w środowisku uruchomieniowym oparty na *MCR.Microsoft.com/dotnet/Core/ASPNET:3.1* jest mały, aby mógł szybko poruszać się w sieci z rejestru Docker do hostów platformy Docker. Zawartość jest gotowa do uruchomienia, co pozwala na najszybszy czas od rozpoczęcia kontenera do przetwarzania wyników. W modelu platformy Docker nie ma potrzeby kompilowania kodu w języku C\#, ponieważ podczas korzystania z programu dotnet Build lub dotnet publish w przypadku używania kontenera kompilacji.

W tym zoptymalizowanym obrazie umieszczane są tylko pliki binarne i inne elementy potrzebne do uruchomienia aplikacji. Na przykład zawartość utworzona przez `dotnet publish` zawiera tylko skompilowane pliki binarne platformy .NET, obrazy,. js i. css. Z biegiem czasu zobaczysz obrazy zawierające przedtrybie JIT (kompilacja z IL do macierzystego, która występuje w czasie wykonywania).

Mimo że istnieje wiele wersji programu .NET Core i obrazów ASP.NET Core, wszystkie współdzielą jedną lub więcej warstw, w tym warstwę bazową. W związku z tym ilość miejsca na dysku wymaganego do przechowywania obrazu jest mała; składa się tylko z różnicy między obrazem niestandardowym i jego obrazem podstawowym. W efekcie można szybko ściągnąć obraz z rejestru.

Podczas eksplorowania repozytoriów obrazów platformy .NET w usłudze Docker Hub można znaleźć wiele wersji obrazów sklasyfikowanych lub oznaczonych tagami. Tagi te pomagają określić, która z nich ma być używana, w zależności od używanej wersji, np. w poniższej tabeli:

| Image (Obraz) | Komentarze |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet:**3,1** | ASP.NET Core, tylko w przypadku środowiska uruchomieniowego i optymalizacje ASP.NET Core, w systemach Linux i Windows (wiele archów) |
| mcr.microsoft.com/dotnet/core/sdk:**3,1** | .NET Core, z dołączonymi zestawami SDK, w systemach Linux i Windows (wiele Arch) |

> [!div class="step-by-step"]
> [Poprzednie](net-container-os-targets.md)
> [dalej](../architect-microservice-container-applications/index.md)
