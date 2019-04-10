---
title: Środowisko deweloperskie dla aplikacji platformy Docker
description: Ustal, jakimi najważniejszych opcjach narzędzia do programowania, które obsługują programowanie platformy Docker w cyklu życia.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3a2fcbe3b9380083622b6ce72cea4bab17d7c2ea
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318824"
---
# <a name="development-environment-for-docker-apps"></a>Środowisko deweloperskie dla aplikacji platformy Docker

## <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzia do opracowywania: Środowiskiem IDE lub edytorem

Niezależnie od tego Jeśli wolisz, pełne i zaawansowanego środowiska IDE lub edytora lekkie i elastyczne, firma Microsoft ma potrzebne, jeśli chodzi o tworzenie aplikacji platformy Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code i interfejsu wiersza polecenia Docker (narzędzi dla wielu platform dla systemów Mac, Linux i Windows)

Jeśli wolisz lekkie Międzyplatformowe Edytor Obsługa dowolnego języka programowania, można użyć programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker. Te produkty zapewniają proste, ale niezawodne środowisko, co ma kluczowe znaczenie dla usprawnienie przepływu pracy dewelopera. Instalując "Docker for Mac" lub "Docker for Windows" (środowisko programistyczne), deweloperzy platformy Docker można użyć pojedynczego interfejsu wiersza polecenia platformy Docker do tworzenia aplikacji Windows lub Linux (środowisko uruchomieniowe). Ponadto w Visual Studio Code obsługuje rozszerzenia dla platformy Docker za pomocą funkcji IntelliSense dla plików Dockerfile i skrót zadania to uruchamianie poleceń Docker z poziomu edytora.

> [!NOTE]
>
> Aby pobrać program Visual Studio Code, przejdź do <https://code.visualstudio.com/download>.
>
> Aby pobrać platformy Docker dla systemów Mac i Windows, przejdź do <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio z narzędziami Docker (komputerze deweloperskim Windows)

Zalecane jest użycie programu Visual Studio 2017 (lub późniejszy) za pomocą wbudowanych narzędzi platformy Docker, włączone. Za pomocą programu Visual Studio mogą tworzyć, uruchamianie i Weryfikuj aplikacje bezpośrednio w wybranym środowisku platformy Docker. Naciśnij klawisz F5, aby debugować aplikację (jeden kontener lub wiele kontenerów) bezpośrednio w hosta platformy Docker lub naciśnij klawisze Ctrl + F5, aby edytować i odświeżać aplikację bez konieczności ponownego kompilowania kontenera. Jest to najprostszy i najbardziej wydajnymi procesorami wybór dla deweloperów Windows do tworzenia kontenerów platformy Docker dla systemu Linux lub Windows.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Program Visual Studio for Mac (komputerze deweloperskim Mac)

Możesz użyć [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) podczas tworzenia aplikacji opartych na platformie Docker. Program Visual Studio for Mac oferuje rozbudowane środowisko IDE, w porównaniu do programu Visual Studio Code dla komputerów Mac.

## <a name="language-and-framework-choices"></a>Opcje języka i struktury

Można tworzyć aplikacje platformy Docker przy użyciu narzędzia Microsoft większość nowoczesnych języków. Poniżej przedstawiono listę początkowej, ale nie trzeba się ograniczać do niego:

- .NET Core i ASP.NET Core
- Node.js
- Z rzeczywistym użyciem
- Java
- Ruby
- Python

Zasadniczo można używać dowolnego języka modern, obsługiwane przez platformę Docker w systemie Linux lub Windows.

>[!div class="step-by-step"]
>[Poprzednie](deploy-azure-kubernetes-service.md)
>[dalej](docker-apps-inner-loop-workflow.md)
