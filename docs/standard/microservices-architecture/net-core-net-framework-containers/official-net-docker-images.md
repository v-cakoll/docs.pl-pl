---
title: Oficjalne obrazy Docker w programie .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Oficjalne obrazy Docker w programie .NET
ms.date: 01/07/2019
ms.openlocfilehash: b184e8f3606da8448a06a1cad90688958ecbce3a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644332"
---
# <a name="official-net-docker-images"></a>Oficjalne obrazy Docker w programie .NET

Obrazy Docker w programie .NET oficjalne są obrazy Docker, utworzone i zoptymalizowane przez firmę Microsoft. Są one dostępne publicznie w przypadku repozytoriów firmy Microsoft na [usługi Docker Hub](https://hub.docker.com/u/microsoft/). Każde repozytorium może zawierać wiele obrazów, w zależności od wersji platformy .NET i w zależności od systemu operacyjnego i wersji (Linux, Debian, Linux Alpine, Windows Nano Server, Windows Server Core, itp.).

Od platformy .NET Core 2.1 wszystkie obrazy platformy .NET Core, w tym dla platformy ASP.NET Core są dostępne w usłudze Docker Hub w repozytorium obrazów platformy .NET Core: https://hub.docker.com/_/microsoft-dotnet-core/

Większość repozytoriów obraz zapewniają szeroką tagowania ułatwiające wybranie nie tylko określonych framework w wersji, ale również wybranie systemu operacyjnego (dystrybucja systemu Linux lub Windows w wersji).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core i Docker optymalizacji obrazu dla rozwoju i produkcji

Podczas tworzenia obrazów platformy Docker dla deweloperów, Microsoft skupia się na następujących głównych scenariuszy:

- Obrazy używane do *opracowywanie* i tworzenie aplikacji .NET Core.

- Obrazy używane do *Uruchom* aplikacje platformy .NET Core.

Dlaczego wiele obrazów? Podczas tworzenia, kompilowania i uruchamiania konteneryzowanych aplikacji, zwykle mają różne priorytety. Dostarczając różne obrazy do oddzielnych wykonywania tych zadań, Microsoft pomaga w optymalizacji oddzielne procesy tworzenia, kompilowania i wdrażania aplikacji.

### <a name="during-development-and-build"></a>Podczas projektowania i kompilowania

Podczas tworzenia aplikacji ważne jest jak szybko można wykonać iterację zmiany i możliwość debugowania zmiany. Rozmiar obrazu nie jest tak ważna jak możliwość zmiany w kodzie i szybko zobaczyć zmiany. Niektóre narzędzia i "kontenery agenta kompilacji", należy użyć obrazu platformy .NET Core development (*mcr.microsoft.com/dotnet/core/sdk:2.2*) podczas procesu projektowania i kompilowania. Podczas kompilowania w kontenerze platformy Docker, ważne kwestie są elementy, które są wymagane w celu kompilowania aplikacji. Obejmuje to kompilator i inne zależności platformy .NET.

Ten typ obrazu kompilacji jest ważna Ten obraz nie są wdrażane do środowiska produkcyjnego. Zamiast tego jest obrazu używanego do tworzenia zawartości, które można umieścić w środowisku produkcyjnym obraz. Ten obraz będzie używany w danym środowisku ciągłej integracji (CI) lub środowiska kompilacji, w przypadku korzystania z platformy Docker wieloetapowych kompilacji.

### <a name="in-production"></a>W środowisku produkcyjnym

Co to jest ważne w środowisku produkcyjnym jest, jak szybko możesz wdrożyć i uruchomić kontenerów opartych na obrazach platformy .NET Core produkcji. W związku z tym, na podstawie obrazu tylko do środowiska uruchomieniowego *mcr.microsoft.com/dotnet/core/aspnet:2.2* jest mały, tak aby rozprzestrzenia się szybko przez sieć z rejestru platformy Docker do hostów platformy Docker. Zawartość jest gotowa do uruchomienia, umożliwiając krótsze czasy uruchamianie kontenera do przetwarzania wyników. W modelu platformy Docker, nie ma potrzeby dla kompilacji z C\# kodu, jako miejsca po uruchomieniu kompilacji dotnet lub opublikować dotnet, kiedy używa kontenerów kompilacji.

W tym zoptymalizowanego obrazu, możesz umieścić tylko pliki binarne i innej zawartości, wymagane do uruchomienia aplikacji. Na przykład publikować zawartość utworzona przez dotnet zawiera tylko skompilowane pliki binarne .NET, obrazy, js i plików CSS. Wraz z upływem czasu, zostanie wyświetlony obrazów, które zawierają wstępnie trybie JIT (kompilacja z IL Native, która występuje w czasie wykonywania) pakietów.

Chociaż istnieje wiele wersji platformy .NET Core i ASP.NET Core obrazów, wszystkie mają jedną lub więcej warstw, łącznie z warstwy podstawowa. W związku z tym ilość miejsca na dysku potrzebnego do przechowywania obrazu jest mała; składa się tylko z różnica między niestandardowego obrazu i jego podstawowego obrazu. Wynik jest szybkie ściągnąć obraz z rejestru.

Podczas eksplorowania repozytoriów obrazu platformy .NET w usłudze Docker Hub znajdziesz wiele wersji obrazu sklasyfikowane lub oznaczona za pomocą tagów. Te znaczniki ułatwić podjęcie decyzji, który z nich do użycia, w zależności od wersji, których potrzebujesz, podobnie jak w poniższej tabeli:

| Obraz                                       | Komentarze                                                                                          |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| MCR.microsoft.com/DotNet/Core/ASPNET:**2.2** | ASP.NET Core przy użyciu tylko środowiska uruchomieniowego i optymalizacje platformy ASP.NET Core, w systemie Linux i Windows (wielu arch) |
| mcr.microsoft.com/dotnet/core/sdk:**2.2**    | .NET core przy użyciu zestawów SDK uwzględnione, w systemie Linux i Windows (wielu arch)                                  |

> [!div class="step-by-step"]
> [Poprzednie](net-container-os-targets.md)
> [dalej](../architect-microservice-container-applications/index.md)
