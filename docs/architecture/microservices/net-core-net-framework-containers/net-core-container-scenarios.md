---
title: Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Kiedy wybrać .NET Core dla kontenerów platformy Docker
ms.date: 01/30/2020
ms.openlocfilehash: f784512af3f520f96d499ab002eda58071b3c284
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147378"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker

Modułowość i lekki charakter .NET Core sprawia, że idealnie nadaje się do kontenerów. Podczas wdrażania i uruchamiania kontenera jego obraz jest znacznie mniejszy z .NET Core niż z .NET Framework. Z drugiej strony, aby użyć programu .NET Framework dla kontenera, należy oprzeć obraz na obrazie Windows Server Core, który jest znacznie cięższy niż obrazy systemu Windows Nano Server lub Linux używane dla programu .NET Core.

Ponadto .NET Core jest wieloplatformowy, dzięki czemu można wdrażać aplikacje serwera z obrazami kontenerów systemu Linux lub Windows. Jednak jeśli używasz tradycyjnej platformy .NET Framework, można wdrażać tylko obrazy na podstawie programu Windows Server Core.

Poniżej przedstawiono bardziej szczegółowe wyjaśnienie, dlaczego warto wybrać .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Opracowywanie i wdrażanie międzyplatformowych

Oczywiście, jeśli twoim celem jest mieć aplikację (aplikacji sieci web lub usługi), które mogą być uruchamiane na wielu platformach obsługiwanych przez platformy Docker (Linux i Windows), właściwym wyborem jest .NET Core, ponieważ .NET Framework obsługuje tylko system Windows.

.NET Core obsługuje również system macOS jako platformę deweloperska. Jednak podczas wdrażania kontenerów na hoście platformy Docker, ten host musi (obecnie) opierać się na systemie Linux lub Windows. Na przykład w środowisku programistycznym można użyć maszyny Wirtualnej systemu Linux uruchomionej na komputerze Mac.

[Visual Studio](https://www.visualstudio.com/vs/) zapewnia zintegrowane środowisko programistyczne (IDE) dla systemu Windows i obsługuje programdocker.

[Visual Studio dla komputerów Mac](https://www.visualstudio.com/vs/visual-studio-mac/) jest IDE, ewolucja Xamarin Studio, który działa na macOS i obsługuje tworzenie aplikacji opartych na platformie Docker. Powinien to być preferowany wybór dla deweloperów pracujących na komputerach Mac, którzy również chcą używać zaawansowanego ide.

Można również użyć [kodu programu Visual Studio](https://code.visualstudio.com/) w systemach macOS, Linux i Windows. Visual Studio Code w pełni obsługuje .NET Core, w tym IntelliSense i debugowania. Ponieważ kod VS jest lekkim edytorem, można go używać do tworzenia konteneryzowanych aplikacji na komputerze Mac w połączeniu z identyfikatorem docker CLI i [.NET Core CLI](../../../core/tools/index.md). Można również kierować .NET Core z większości edytorów innych firm, takich jak Sublime, Emacs, vi i open-source OmniSharp projektu, który zapewnia również obsługę IntelliSense.

Oprócz ides i edytorów, można użyć [.NET Core CLI](../../../core/tools/index.md) dla wszystkich obsługiwanych platform.

## <a name="using-containers-for-new-green-field-projects"></a>Korzystanie z kontenerów dla nowych projektów ("zielone pole")

Kontenery są często używane w połączeniu z architekturą mikrousług, chociaż mogą być również używane do konteneryzacji aplikacji sieci web lub usług, które są zgodne z dowolnym wzorcem architektury. Można użyć .NET Framework w kontenerach systemu Windows, ale modułowość i lekki charakter .NET Core sprawia, że jest idealny dla kontenerów i architektur mikrousług. Podczas tworzenia i wdrażania kontenera jego obraz jest znacznie mniejszy z .NET Core niż w .NET Framework.

## <a name="create-and-deploy-microservices-on-containers"></a>Tworzenie i wdrażanie mikrousług w kontenerach

Można użyć tradycyjnej platformy .NET Framework do tworzenia aplikacji opartych na mikrousługach (bez kontenerów) przy użyciu zwykłych procesów. W ten sposób, ponieważ .NET Framework jest już zainstalowany i współużytkowany między procesami, procesy są lekkie i szybkie, aby rozpocząć. Jednak jeśli używasz kontenerów, obraz dla tradycyjnej platformy .NET Framework jest również oparty na Windows Server Core i sprawia, że zbyt ciężkie dla podejścia mikrousług na kontenerach. Jednak zespoły szukały możliwości poprawy środowiska dla użytkowników .NET Framework, jak również. Ostatnio rozmiar obrazów [kontenerów Windows Server Core został zmniejszony do >o 40% mniejszy](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller).

Z drugiej strony .NET Core jest najlepszym kandydatem, jeśli ogarniasz system zorientowany na mikrousługi, który jest oparty na kontenerach, ponieważ .NET Core jest lekki. Ponadto powiązane obrazy kontenerów, dla systemu Linux lub Windows Nano Server, są chude i małe, dzięki czemu kontenery są lekkie i szybkie.

Mikrousługi ma być tak małe, jak to możliwe: być lekki podczas przędzenia, mieć mały rozmiar, aby mieć mały ograniczony kontekst (sprawdź DDD, [Domain-Driven Design),](https://en.wikipedia.org/wiki/Domain-driven_design)aby reprezentować niewielki obszar problemów i być w stanie uruchomić i zatrzymać szybko. Dla tych wymagań należy użyć małych i szybko wystąpienia obrazów kontenera, takich jak obraz kontenera .NET Core.

Architektura mikrousług umożliwia również łączenie technologii przez granicę usługi. Umożliwia to stopniową migrację do .NET Core dla nowych mikrousług, które działają w połączeniu z innymi mikrousługami lub z usługopracowanych za pomocą Node.js, Python, Java, GoLang lub innych technologii.

## <a name="deploying-high-density-in-scalable-systems"></a>Wdrażanie systemów o dużej gęstości w systemach skalowalnych

Gdy system oparty na kontenerach potrzebuje najlepszej możliwej gęstości, szczegółowości i wydajności, najlepszymi opcjami są .NET Core i ASP.NET Core. ASP.NET Core jest do dziesięciu razy szybszy niż ASP.NET w tradycyjnej platformie .NET Framework i prowadzi inne popularne technologie branżowe dla mikrousług, takie jak serwlety Java, Go i Node.js.

Jest to szczególnie istotne dla architektury mikrousług, gdzie może mieć setki mikrousług (kontenerów) uruchomione. Dzięki ASP.NET obrazów Core (opartych na środowiskach uruchomieniowych .NET Core) w systemie Linux lub Windows Nano można uruchomić system przy znacznie mniejszej liczbie serwerów lub maszyn wirtualnych, co ostatecznie pozwala zaoszczędzić koszty infrastruktury i hostingu.

>[!div class="step-by-step"]
>[Poprzedni](general-guidance.md)
>[następny](net-framework-container-scenarios.md)
