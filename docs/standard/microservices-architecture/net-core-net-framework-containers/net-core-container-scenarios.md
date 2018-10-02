---
title: Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: fa5efd3c2478965ef01efc39b57918ec2d35962a
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862947"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker

Charakter modułowości i uproszczonego programu .NET Core sprawia, że doskonałe dla kontenerów. Podczas wdrażanie i uruchamianie kontenera, obraz jest znacznie mniejszy z platformą .NET Core niż za pomocą .NET Framework. Z kolei używać .NET Framework dla kontenera, należy utworzyć obraz na obrazu systemu Windows Server Core, który jest znacznie większych niż Windows Nano Server lub obrazów systemu Linux, których używasz dla platformy .NET Core.

Ponadto platforma .NET Core to dla wielu platform, dzięki czemu można wdrażać aplikacji serwera przy użyciu obrazów kontenerów systemu Linux lub Windows. Jednak jeśli używasz tradycyjnych .NET Framework, można wdrażać tylko obrazy oparte na systemie Windows Server Core.

Oto bardziej szczegółowe wyjaśnienie, dlaczego wybrać oprogramowanie .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Tworzenie i wdrażanie wiele platform

Wyraźnie widać Jeśli celem jest zapewnienie aplikacji (aplikacji sieci web lub usługi), która może działać na wielu platformach obsługiwanych przez platformę Docker w systemie Linux i Windows, właściwym wyborem jest platformy .NET Core, ponieważ program .NET Framework obsługuje tylko Windows.

.NET core obsługuje również system macOS jako platformy projektowej. Jednak podczas wdrażania kontenerów hosta platformy Docker tego hosta musi (obecnie) oparta na systemie Linux lub Windows. Na przykład w środowisku deweloperskim, możesz użyć maszyny Wirtualnej systemu Linux uruchomiony na komputerze Mac.

[Program Visual Studio](https://www.visualstudio.com/vs/) udostępnia zintegrowanym środowisku programistycznym (IDE) dla Windows i wspiera rozwój platformy Docker.

[Program Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) to środowisko IDE, rozwoju programu Xamarin Studio, która działa w systemie macOS i obsługuje opracowywanie aplikacji opartych na platformie Docker. Powinna to być preferowanych przez dla deweloperów pracujących w komputerów Mac, również chcą korzystać z zaawansowanego środowiska IDE.

Można również użyć [programu Visual Studio Code](https://code.visualstudio.com/) (VS Code) w systemach macOS, Linux i Windows. Program VS Code w pełni obsługuje platformę .NET Core, w tym funkcji IntelliSense i debugowania. Ponieważ program VS Code to lekki edytor, służy do tworzenia konteneryzowanych aplikacji na komputerze Mac w połączeniu z interfejsem wiersza polecenia platformy Docker i [platformy .NET Core interfejsu wiersza polecenia (CLI)](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x). Możesz również kierować platformy .NET Core za pomocą edytorów większości firm, takich jak Sublime, Emacs vi i projekt technologię OmniSharp typu open source, który obsługuje technologię IntelliSense.

Oprócz środowiska IDE i edytorów, można użyć [interfejsu wiersza polecenia platformy .NET Core](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) narzędzia dla wszystkich obsługiwanych platform.

## <a name="using-containers-for-new-green-field-projects"></a>Używanie kontenerów dla nowych projektów ("pole zielony")

Kontenery są często używane w połączeniu z architektury mikrousług, mimo że one może również służyć do konteneryzowanie aplikacji sieci web lub usługi, które należy wykonać wszelkie wzorzec architektury. .NET Framework można używać na kontenery Windows, ale Modułowość i charakter uproszczonego programu .NET Core sprawia, że doskonale dla architektur mikrousług i kontenerów. Podczas tworzenia i wdrażania kontenera jego obraz jest znacznie mniejszy z platformą .NET Core niż za pomocą .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Tworzenie i wdrażanie mikrousług w kontenerach

Można użyć do tworzenia aplikacji opartych na mikrousługach (bez kontenery) przy użyciu zwykłego procesy tradycyjnych .NET Framework. W ten sposób, ponieważ programu .NET Framework jest już zainstalowany i współużytkowane przez procesy, procesy są stosunkowo i szybkie, aby rozpocząć. Jednak korzystania z kontenerów obrazu dla tradycyjnych .NET Framework również opiera się na systemie Windows Server Core, i dzięki temu zbyt duże, podejście mikrousług w kontenerach.

Z kolei platformy .NET Core jest najlepszej sugestii, jeśli są stosujących zorientowanych na mikrousługi systemu, który jest oparty na kontenerach, ponieważ platforma .NET Core to uproszczone. Ponadto obrazy powiązane kontenera, obraz systemu Linux lub obrazu systemu Windows Nano to odchudzona i małe, wprowadzania światła kontenerów i szybko zacząć.

Mikrousługi można w dużym możliwie najmniejsze: o niewielkich rozmiarach, ma mały kontekstu ograniczonego, aby być światła, gdy wdrażanie (Sprawdź DDD, [projektowania driven](https://en.wikipedia.org/wiki/Domain-driven_design)) do reprezentowania mały obszar problemów i aby można było uruchomić i szybkie zatrzymanie. Te wymagania należy używać obrazów małe i szybko wystąpienia kontenera, takich jak obraz kontenera platformy .NET Core.

Architektura mikrousług umożliwia także mieszać technologii granicę usługi. Dzięki temu Stopniowa migracja do programu .NET Core dla nowych mikrousług, które działają w połączeniu z innymi mikrousług lub usług opracowanych za pomocą środowiska Node.js, Python, Java, języku GoLang lub inne technologie.

## <a name="deploying-high-density-in-scalable-systems"></a>Skalowalne systemy wdrożenia o wysokiej gęstości

Gdy opartych na kontenerach systemu musi najlepsze możliwe gęstości, poziom szczegółowości i wydajności, .NET Core i ASP.NET Core są najlepsze opcje. Platforma ASP.NET Core to do dziesięciu razy szybciej niż platformy ASP.NET w tradycyjnych .NET Framework i prowadzi inne technologie popularnych branży mikrousług, takich jak serwletów języka Java, Go i Node.js.

Jest to szczególnie istotne dla architektury mikrousług, gdzie mogą istnieć setki mikrousługi (kontenery) uruchomiona. Przy użyciu platformy ASP.NET Core obrazów (oparte na środowisko uruchomieniowe platformy .NET Core) w systemie Linux lub Windows Nano możesz uruchomić systemu za pomocą znacznie mniejszej liczby serwerów lub maszyn wirtualnych, ostatecznie minimalizując koszty w infrastrukturze i hostingu.


>[!div class="step-by-step"]
[Poprzednie](general-guidance.md)
[dalej](net-framework-container-scenarios.md)
