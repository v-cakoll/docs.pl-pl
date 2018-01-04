---
title: "Oficjalna obrazy usługi .NET Docker"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Oficjalna obrazy usługi .NET Docker"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42872caa1a9306187daeefd35feb9bec3fae60af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="official-net-docker-images"></a>Oficjalna obrazy usługi .NET Docker

Obrazy oficjalnego Docker .NET są obrazy usługi Docker utworzone i zoptymalizowane przez firmę Microsoft. Są one dostępne publicznie w repozytoriach Microsoft [Centrum Docker](https://hub.docker.com/u/microsoft/). Każdego repozytorium może zawierać wiele obrazów, w zależności od wersji platformy .NET, a także w zależności od systemu operacyjnego i wersji (Linux Debian, Alpine systemu Linux, Windows Nano Server, Windows Server Core, itp.).

Wizji firmy Microsoft dla repozytoriów .NET jest szczegółowym i skupiają się repozytoriów, gdzie repozytorium reprezentuje konkretnych sytuacji lub obciążenia. Na przykład [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) obrazów powinna być używana, jeśli przy użyciu platformy ASP.NET Core na Docker, ponieważ te obrazy platformy ASP.NET Core udostępniają dodatkowe optymalizacje tak kontenery można uruchomić szybciej.

Z drugiej strony obrazy .NET Core (microsoft/dotnet) są przeznaczone dla aplikacji konsoli .NET Core w oparciu. Na przykład procesy partii zadań Webjob Azure i inne scenariusze konsoli, należy użyć .NET Core. Tych obrazów nie dołączaj stosu platformy ASP.NET Core, co powoduje mniejsze obrazu kontenera.

Większość repozytoriów obrazu zapewniają szeroką gamę znakowanie ułatwiające wybranie nie tylko wersji określonej platformy, ale wybierz system operacyjny (Linux distro lub wersji systemu Windows).

Aby uzyskać więcej informacji o obrazach .NET Docker oficjalnego obsługiwane przez firmę Microsoft, zobacz [podsumowanie obrazy usługi Docker .NET](https://aka.ms/dotnetdockerimages).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Oprogramowanie .NET core i Docker optymalizacji obrazu dla rozwoju i produkcji

Tworząc obrazy usługi Docker dla deweloperów, Microsoft skupia się na następujących głównych scenariuszy:

-   Obrazy używane do *opracowanie* i tworzenie aplikacji platformy .NET Core.

-   Obrazy używane do *Uruchom* aplikacje .NET Core.

Dlaczego wiele obrazów? Podczas tworzenia, tworzenie i uruchamianie aplikacji konteneryzowanych, zwykle mają różnych priorytetów. Podając inną obrazy te poszczególnych zadań, Microsoft pomaga zoptymalizować oddzielne procesy tworzenia, kompilowania i wdrażania aplikacji.

### <a name="during-development-and-build"></a>Podczas projektowania i kompilacji

Podczas tworzenia ważne jest tempa można wykonać iterację zmiany i możliwość zmiany debugowania. Rozmiar obrazu nie jest ważniejsza niż możliwość wprowadzić zmiany w kodzie i szybko zobaczyć zmiany. Niektóre narzędzia i "kontenery agenta kompilacji", użyj programowanie obrazu platformy ASP.NET Core (microsoft aspnetcore kompilacji) podczas tworzenia i proces kompilacji. Podczas kompilowania w kontenerze Docker, ważne kwestie związane są elementy, które są wymagane, aby skompilować aplikację. Obejmuje to kompilator i wszelkich innych zależności .NET, a także zależności programowanie sieci web, takich jak npm, system Gulp i Bower.

Ten typ obrazu kompilacji jest ważna Ten obraz nie są wdrażane w środowisku produkcyjnym. Zamiast tego jest obraz, który umożliwia tworzenie zawartości, który można umieścić w środowisku produkcyjnym obraz. Ten obraz będzie używany w danym środowisku ciągłej integracji (CI) lub środowisko kompilacji. Na przykład zamiast ręcznego instalowania zależności aplikacji bezpośrednio na agenta kompilacji hosta (maszyn wirtualnych, na przykład), agent kompilacji będzie wystąpienia obrazu kompilacji platformy .NET Core wszystkie zależności wymagane do tworzenia aplikacji. Agenta kompilacji musi znać tylko sposób uruchamiania tego obrazu Docker. Upraszcza środowiska CI to i ułatwia znacznie bardziej przewidywalne.

### <a name="in-production"></a>W środowisku produkcyjnym

Co to jest ważne w środowisku produkcyjnym jest tempa można wdrożyć i uruchomić kontenerów na podstawie obrazu platformy .NET Core produkcji. W związku z tym, na podstawie obrazu tylko do środowiska wykonawczego [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) jest mały, dzięki czemu rozprzestrzenia się szybko w sieci z rejestru Docker na hostach Docker. Zawartość jest gotowy do uruchomienia, włączanie o najszybszym czasie uruchamianiu kontenera do przetwarzania wyników. W modelu Docker nie jest wymagane do kompilacji z C\# kodu, ponieważ wystąpiły po uruchomieniu dotnet kompilacji lub dotnet publikowania, gdy używa kontenera kompilacji.

W tym zoptymalizowanego obrazu możesz umieścić tylko pliki binarne i innej zawartości, wymaganego do uruchomienia aplikacji. Na przykład zawartość utworzona przez dotnet opublikować zawiera tylko skompilowanych .NET pliki binarne, obrazy, js i pliki CSS. W czasie zostanie wyświetlony obrazów zawierających pakiety poprzedzającego utworzenie kopii zapasowej przy użyciu kompilatora JIT.

Mimo że istnieje wiele wersji .NET Core i ASP.NET Core obrazów, wszystkie mają jednej lub kilku warstw, łącznie z warstwy podstawowej. W związku z tym ilość miejsca na dysku wymagane do przechowywania obrazu jest mała; składa się tylko z różnica między niestandardowego obrazu i jego obrazu podstawowego. Wynik jest szybkie do pobierania obrazu z rejestru.

Podczas eksplorowania repozytoria obrazu platformy .NET w Centrum Docker można znaleźć wiele wersji obrazu sklasyfikowane lub oznaczone tagami. Tagi te pomogą zdecydować, który z nich do używania w zależności od wersji, które są potrzebne, podobnie jak w poniższej tabeli:

-   Microsoft /**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**aspnetcore-kompilacji: 2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Poprzednie] (net kontenera os-targets.md) [dalej] (.. /Architect-microservice-container-Applications/index.MD)
