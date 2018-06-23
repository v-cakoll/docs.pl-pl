---
title: Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 45917a9dbfbd6610c3cca9ab7dcf9f924c329c10
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314929"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker

Modułowości i lightweight rodzaj .NET Core sprawia, że idealne dla kontenerów. Wdrażania i uruchomić kontener, jego obrazu jest znacznie mniejszy z platformą .NET Core niż platformy .NET Framework. Z kolei używanie środowiska .NET Framework dla kontenera, należy utworzyć obraz w obrazie systemu Windows Server Core, czyli znacznie większych niż Windows Nano Server lub Linux obrazów, używane dla platformy .NET Core.

Ponadto oprogramowanie .NET Core jest między platformami, więc można wdrażać aplikacje serwera z systemem Linux lub Windows obrazami kontenera. Jednak jeśli korzystasz z tradycyjnego .NET Framework, można wdrażać tylko obrazy oparte na systemie Windows Server Core.

Poniżej znajduje się bardziej szczegółowy opis dlaczego wybierz .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Tworzenie i wdrażanie cross platform

Wyraźnie widać jeśli mają być aplikacji (aplikacji sieci web lub usługi), która może działać na wielu platformach obsługiwanych przez Docker (Linux i Windows), warto wybrać jest .NET Core, ponieważ .NET Framework obsługuje tylko systemu Windows.

Oprogramowanie .NET core obsługuje również system macOS jako platformy programistycznej. Jednak gdy wdrożeniem kontenerów do hostów Docker hostujących musi (obecnie) oparta na Linux lub Windows. Na przykład w środowisku programowania można użyć maszyny Wirtualnej systemu Linux uruchomionych na komputerach Mac.

[Visual Studio](https://visualstudio.microsoft.com/) zapewnia zintegrowane środowisko programistyczne (IDE) dla systemu Windows i obsługuje programowanie Docker. 

[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/) IDE ewolucja platformy Xamarin Studio, uruchomionych w macOS i obsługuje od połowy 2017 Docker.

Można również użyć [Visual Studio Code](https://code.visualstudio.com/) (kodzie VS) na macOS, Linux i Windows. Kod programu VS w pełni obsługuje .NET Core, w tym IntelliSense i debugowania. Ponieważ kodzie VS jest lekki edytora, można użyć go do opracowywania aplikacji konteneryzowanych na Mac w połączeniu z poziomu interfejsu wiersza polecenia Docker i [narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core](../../../core/tools/index.md). Można również docelowych .NET Core edytory najbardziej innych firm, takich jak Sublime tekstu, Emacs vi i OmniSharp projekt open source, co zapewnia obsługę funkcji IntelliSense dla języków .NET. Oprócz IDEs i edytory można użyć interfejsu wiersza polecenia platformy .NET Core dla wszystkich obsługiwanych platformach.

## <a name="using-containers-for-new-green-field-projects"></a>Używanie kontenerów dla nowych projektów ("pole zielony")

Kontenery są często używane w połączeniu z architekturą mikrousług, chociaż są one może również służyć do containerize aplikacji sieci web lub usługi, które należy wykonać wszelkie wzorzec architektury. Kontenery systemu Windows, ale Modułowość służy .NET Framework i lekkie rodzaj .NET Core sprawia, że idealne w przypadku architektury kontenery i mikrousług. Podczas tworzenia i wdrażania kontener jego obrazu jest znacznie mniejszy z platformą .NET Core niż platformy .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Tworzenie i wdrażanie mikrousług kontenerów

Tradycyjny .NET Framework można użyć do tworzenia aplikacji opartych na mikrousług (bez kontenery) przy użyciu zwykłego procesów. W ten sposób, ponieważ programu .NET Framework jest już zainstalowany i współużytkowane przez procesy, procesy są jasny i szybko uruchomić. Jednak jeśli używasz kontenery obrazu dla tradycyjnych .NET Framework opiera się również w systemie Windows Server Core i dzięki temu zbyt duże podejścia mikrousług na kontenerów.

Z kolei .NET Core jest najlepszej sugestii, jeśli są obejmującego zorientowane na mikrousług systemu, w którym jest oparty na kontenery, ponieważ jest lekki .NET Core. Ponadto jego kontenera powiązane obrazów, obraz systemu Linux lub obrazu systemu Windows Nano są gotowa i małych wprowadzania jasny kontenery i szybkie, aby rozpocząć.

Mikrousługi ma być możliwie jak najmniejszy: jest lekki, gdy kręci się, aby mieć niewielkie rozmiary, mieć małych ograniczone kontekst — do reprezentowania mały obszar problemy oraz aby można było uruchomić i zatrzymać szybkie. Te wymagania należy używać obrazów kontenera małych i fast wystąpienia takich jak obraz kontenera .NET Core.

Architektura mikrousług umożliwia także mieszać technologii granicy usługi. Dzięki temu stopniowej migracji do .NET Core dla nowych mikrousług, które działają w połączeniu z innymi mikrousług lub z usługami opracowany ze środowiska Node.js, Python, Java, GoLang ani innych technologii.

## <a name="deploying-high-density-in-scalable-systems"></a>Wdrażanie w skalowalne systemy o wysokiej gęstości

Gdy systemu kontenera musi najlepsze możliwe gęstość, poziom szczegółowości i wydajności, oprogramowanie .NET Core i ASP.NET Core są najlepsze opcje. Platformy ASP.NET Core jest maksymalnie 10 razy szybsze niż ASP.NET w tradycyjnych .NET Framework i prowadzi innych popularnych branżowymi technologiami dla mikrousług, takie jak servlets Java, podróży i Node.js.

Jest to szczególnie istotne dla architektury mikrousług, gdzie mogą być setki mikrousług (kontenery) uruchomione. Za pomocą platformy ASP.NET Core obrazów (w oparciu środowiska uruchomieniowego .NET Core) w systemie Linux lub Nano systemu Windows można uruchomić system ze znacznie mniejszą liczbę serwerów lub maszyn wirtualnych, a ostatecznie zapisaniem kosztów infrastruktury i hostingu.


>[!div class="step-by-step"]
[Poprzednie] (Ogólne guidance.md) [dalej] (net-framework — kontener scenarios.md)
