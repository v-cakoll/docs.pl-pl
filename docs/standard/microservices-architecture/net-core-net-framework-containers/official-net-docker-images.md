---
title: Oficjalna obrazy usługi .NET Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Oficjalna obrazy usługi .NET Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 8664493f3d5d5e03cccbe1c33f2c2abe048e3f57
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105579"
---
# <a name="official-net-docker-images"></a>Oficjalna obrazy usługi .NET Docker

Obrazy oficjalnego Docker .NET są obrazy usługi Docker utworzone i zoptymalizowane przez firmę Microsoft. Są one dostępne publicznie w repozytoriach Microsoft [Centrum Docker](https://hub.docker.com/u/microsoft/). Każdego repozytorium może zawierać wiele obrazów, w zależności od wersji platformy .NET, a także w zależności od systemu operacyjnego i wersji (Linux Debian, Alpine systemu Linux, Windows Nano Server, Windows Server Core, itp.).

Ponieważ .NET Core 2.1, wszystkie obrazy .NET Core, w tym dla platformy ASP.NET Core są dostępne pod adresem Centrum Docker na [repozytorium obrazu platformy .NET Core](https://hub.docker.com/r/microsoft/dotnet/).

Większość repozytoriów obrazu zapewniają szeroką gamę znakowanie ułatwiające wybranie nie tylko wersji określonej platformy, ale wybierz system operacyjny (Linux distro lub wersji systemu Windows).


## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Oprogramowanie .NET core i Docker optymalizacji obrazu dla rozwoju i produkcji

Tworząc obrazy usługi Docker dla deweloperów, Microsoft skupia się na następujących głównych scenariuszy:

-   Obrazy używane do *opracowanie* i tworzenie aplikacji platformy .NET Core.

-   Obrazy używane do *Uruchom* aplikacje .NET Core.

Dlaczego wiele obrazów? Podczas tworzenia, tworzenie i uruchamianie aplikacji konteneryzowanych, zwykle mają różnych priorytetów. Podając inną obrazy te poszczególnych zadań, Microsoft pomaga zoptymalizować oddzielne procesy tworzenia, kompilowania i wdrażania aplikacji.

### <a name="during-development-and-build"></a>Podczas projektowania i kompilacji

Podczas tworzenia ważne jest tempa można wykonać iterację zmiany i możliwość zmiany debugowania. Rozmiar obrazu nie jest ważniejsza niż możliwość wprowadzić zmiany w kodzie i szybko zobaczyć zmiany. Niektóre narzędzia i "kontenery agenta kompilacji", użyj programowanie obrazu platformy ASP.NET Core (**microsoft / dotnet:2.1-sdk**) podczas procesu projektowania i kompilacji. Podczas kompilowania w kontenerze Docker, ważne kwestie związane są elementy, które są wymagane, aby skompilować aplikację. W tym kompilator żadnych innych zależności .NET, a także zależności Projektowanie sieci web.

Ten typ obrazu kompilacji jest ważna Ten obraz nie są wdrażane w środowisku produkcyjnym. Zamiast tego jest obraz, który umożliwia tworzenie zawartości, który można umieścić w środowisku produkcyjnym obraz. Czy można użyć tego obrazu w danym środowisku ciągłej integracji (CI) lub kompilacje środowiska kompilacji, używając wieloetapowym Docker.

### <a name="in-production"></a>W środowisku produkcyjnym

Co to jest ważne w środowisku produkcyjnym jest tempa można wdrożyć i uruchomić kontenerów na podstawie obrazu platformy .NET Core produkcji. W związku z tym, na podstawie obrazu tylko do środowiska wykonawczego **microsoft / dotnet:2.1 — aspnetcore — środowisko uruchomieniowe** jest mały, dzięki czemu rozprzestrzenia się szybko w sieci z rejestru Docker na hostach Docker. Zawartość jest gotowy do uruchomienia, włączanie o najszybszym czasie uruchamianiu kontenera do przetwarzania wyników. W modelu Docker nie jest wymagane do kompilacji z C\# kodu, ponieważ wystąpiły po uruchomieniu dotnet kompilacji lub dotnet publikowania, gdy używa kontenera kompilacji.

W tym zoptymalizowanego obrazu możesz umieścić tylko pliki binarne i innej zawartości, wymaganego do uruchomienia aplikacji. Na przykład zawartość utworzona przez dotnet opublikować zawiera tylko skompilowanych .NET pliki binarne, obrazy, js i pliki CSS. W czasie zostanie wyświetlony obrazów zawierających pakiety poprzedzającego utworzenie kopii zapasowej przy użyciu kompilatora JIT.

Mimo że istnieje wiele wersji .NET Core i ASP.NET Core obrazów, wszystkie mają jednej lub kilku warstw, łącznie z warstwy podstawowej. W związku z tym ilość miejsca na dysku wymagane do przechowywania obrazu jest mała; składa się tylko z różnica między niestandardowego obrazu i jego obrazu podstawowego. Wynik jest szybkie do pobierania obrazu z rejestru.

Podczas eksplorowania repozytoria obrazu platformy .NET w Centrum Docker można znaleźć wiele wersji obrazu sklasyfikowane lub oznaczone tagami. Tagi te pomogą zdecydować, który z nich do używania w zależności od wersji, które są potrzebne, podobnie jak w poniższej tabeli:

-   Microsoft/dotnet:**2.1-aspnetcore — środowisko uruchomieniowe**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**dotnet:2.1-sdk**

        .NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Poprzednie](net-container-os-targets.md)
[dalej](../architect-microservice-container-applications/index.md)
