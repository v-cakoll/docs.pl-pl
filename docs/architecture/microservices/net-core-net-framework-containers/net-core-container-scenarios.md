---
title: Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Kiedy należy wybrać platformę .NET Core dla kontenerów platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 54ed1b4bbb16352b8c99204383f85ffb25d62be7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296501"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kiedy należy wybrać oprogramowanie .NET Core dla kontenerów Docker

Modularność i lekki charakter platformy .NET Core sprawia, że jest idealnym rozwiązaniem dla kontenerów. Po wdrożeniu i uruchomieniu kontenera jego obraz jest znacznie mniejszy od platformy .NET Core niż z .NET Framework. Z drugiej strony, aby użyć .NET Framework dla kontenera, należy oprzeć obraz na podstawowym obrazie systemu Windows Server, który jest dużo większy niż obrazy systemu Windows nano Server lub Linux, które są używane dla platformy .NET Core.

Ponadto platforma .NET Core jest międzyplatformowa, dzięki czemu można wdrażać aplikacje serwera przy użyciu obrazów z systemem Linux lub Windows. Jeśli jednak używasz tradycyjnego .NET Framework, możesz wdrażać tylko obrazy oparte na systemie Windows Server Core.

Poniżej znajduje się bardziej szczegółowy opis dlaczego należy wybrać platformę .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Tworzenie i wdrażanie wielu platform

Jasno, jeśli celem jest posiadanie aplikacji (aplikacji sieci Web lub usługi), która może być uruchamiana na wielu platformach obsługiwanych przez platformę Docker (Linux i Windows), właściwy wybór to .NET Core, ponieważ .NET Framework obsługuje tylko system Windows.

Program .NET Core obsługuje również macOS jako platformę programistyczną. Jednak podczas wdrażania kontenerów na hoście platformy Docker ten host musi (obecnie) być oparty na systemie Linux lub Windows. Na przykład w środowisku deweloperskim można użyć maszyny wirtualnej z systemem Linux działającej na komputerze Mac.

[Program Visual Studio](https://www.visualstudio.com/vs/) udostępnia zintegrowane środowisko programistyczne (IDE) dla systemu Windows i obsługuje programowanie platformy Docker.

[Visual Studio dla komputerów Mac](https://www.visualstudio.com/vs/visual-studio-mac/) to IDE, ewolucja Xamarin Studio, która działa w macOS i obsługuje tworzenie aplikacji opartych na platformie Docker. Powinno to być preferowany wybór dla deweloperów pracujących na komputerach Mac, którzy chcą również korzystać z zaawansowanego środowiska IDE.

Możesz również użyć [Visual Studio Code](https://code.visualstudio.com/) (vs Code) w systemach MacOS, Linux i Windows. VS Code w pełni obsługuje platformę .NET Core, w tym IntelliSense i debugowanie. Ponieważ VS Code jest lekkim edytorem, można go użyć do tworzenia kontenerów aplikacji na komputerach Mac w połączeniu z [interfejsem wiersza polecenia platformy](../../../core/tools/index.md)Docker i .NET Core. Możesz również wskazać platformę .NET Core za pomocą większości edytorów innych firm, takich jak subwapno, Emacs:, VI i projekt typu open source OmniSharp, który oferuje również obsługę technologii IntelliSense.

Oprócz środowisk IDE i edytorów, można użyć narzędzi [interfejs wiersza polecenia platformy .NET Core](../../../core/tools/index.md) dla wszystkich obsługiwanych platform.

## <a name="using-containers-for-new-green-field-projects"></a>Używanie kontenerów dla nowych projektów ("zielony-pole")

Kontenery są często używane w połączeniu z architekturą mikrousług, chociaż mogą być również używane do konteneryzowanie aplikacji lub usług sieci Web, które są zgodne z dowolnym wzorcem architektury. .NET Framework w kontenerach systemu Windows, ale modularność i lekki charakter platformy .NET Core sprawia, że jest idealnym rozwiązaniem w przypadku kontenerów i architektur mikrousług. Po utworzeniu i wdrożeniu kontenera jego obraz jest znacznie mniejszy przy użyciu platformy .NET Core niż z .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Tworzenie i wdrażanie mikrousług w kontenerach

Można użyć tradycyjnego .NET Framework do tworzenia aplikacji opartych na mikrousługach (bez kontenerów) za pomocą zwykłych procesów. Dzięki temu, ponieważ .NET Framework są już zainstalowane i udostępniane między procesami, procesy są jasne i szybkie, aby rozpocząć. Jeśli jednak korzystasz z kontenerów, obraz dla tradycyjnych .NET Framework jest również oparty na systemie Windows Server Core i sprawia, że jest zbyt ciężki dla podejścia mikrousługowego na kontenery.

W przeciwieństwie do programu .NET Core jest najlepszym kandydatem, jeśli korzystasz z systemu opartego na mikrousługach opartych na kontenerach, ponieważ .NET Core jest lekki. Ponadto powiązane z nimi obrazy kontenerów, obraz systemu Linux lub obraz Windows nano, to oszczędne i małe tworzenie pojemników, jasne i szybkie.

Mikrousługa powinna być możliwie najmniejsza, jak to możliwe, aby było jasne, aby mieć niewielki wpływ na niewielką część (sprawdzanie DDD, [Projektowanie oparte na domenie](https://en.wikipedia.org/wiki/Domain-driven_design)), aby reprezentować mały obszar wątpliwości i mieć możliwość szybkiego uruchamiania i zatrzymywania. W przypadku tych wymagań należy użyć małych i szybkich obrazów kontenerów, takich jak obraz kontenera .NET Core.

Architektura mikrousług umożliwia również mieszanie technologii między granicami usług. Dzięki temu można stopniowo przeprowadzić migrację do platformy .NET Core dla nowych mikrousług, które działają w połączeniu z innymi mikrousługami lub usługami opracowanymi przy użyciu technologii Node. js, Python, Java, GoLang lub innych.

## <a name="deploying-high-density-in-scalable-systems"></a>Wdrażanie wysokiej gęstości w skalowalnych systemach

Gdy system oparty na kontenerach wymaga najlepszej możliwej gęstości, szczegółowości i wydajności, program .NET Core i ASP.NET Core są najlepszymi opcjami. ASP.NET Core jest nawet dziesięć razy szybsze niż ASP.NET w tradycyjnych .NET Framework i prowadzi do innych popularnych technologii branżowych dla mikrousług, takich jak Java serwletów, go i Node. js.

Jest to szczególnie istotne w przypadku architektury mikrousług, w których można korzystać z setek mikrousług (kontenerów). W przypadku obrazów ASP.NET Core (opartych na środowisku uruchomieniowym .NET Core) w systemie Linux lub Windows nano można uruchomić system z znacznie mniejszą liczbą serwerów lub maszyn wirtualnych, co ostatecznie oszczędza koszty infrastruktury i hostingu.

>[!div class="step-by-step"]
>[Poprzedni](general-guidance.md)
>[Następny](net-framework-container-scenarios.md)
