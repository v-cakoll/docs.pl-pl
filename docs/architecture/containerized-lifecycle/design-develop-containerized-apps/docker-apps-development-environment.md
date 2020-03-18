---
title: Środowisko deweloperskie dla aplikacji platformy Docker
description: Poznaj najważniejsze opcje narzędzi programistycznych, które obsługują cykl życia rozwoju platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71214302"
---
# <a name="development-environment-for-docker-apps"></a>Środowisko deweloperskie dla aplikacji platformy Docker

## <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzi programistycznych: IDE lub edytor

Bez względu na to, czy wolisz pełny i wydajny IDE lub lekki i zwinny edytor, Microsoft ma Cię w około prawie, jeśli chodzi o tworzenie aplikacji Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code i Docker CLI (narzędzia międzyplatformowe dla komputerów Mac, Linux i Windows)

Jeśli wolisz lekki edytor między platformami obsługujący dowolny język deweloperski, możesz użyć kodu programu Visual Studio i identyfikatora docker CLI. Produkty te zapewniają proste, ale niezawodne środowisko, które ma kluczowe znaczenie dla usprawnienia przepływu pracy dla deweloperów. Instalując "Docker for Mac" lub "Docker for Windows" (środowisko programistyczne), deweloperzy platformy Docker mogą używać jednego środowiska cli platformy Docker do tworzenia aplikacji dla systemu Windows lub Linux (środowisko środowiska uruchomieniowego). Ponadto program Visual Studio Code obsługuje rozszerzenia platformy Docker z intelliSense dla plików dockerfiles i zadania skrótów do uruchamiania poleceń platformy Docker z edytora.

> [!NOTE]
> Aby pobrać kod programu <https://code.visualstudio.com/download>Visual Studio, przejdź do .
>
> Aby pobrać platformę Docker dla <https://www.docker.com/products/docker>komputerów Mac i system Windows, przejdź do witryny .

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio z narzędziami platformy Docker (komputer deweloperskie systemu Windows)

Zaleca się używanie programu Visual Studio 2017 (lub nowszego) z włączonymi wbudowanymi narzędziami platformy Docker. Za pomocą programu Visual Studio można tworzyć, uruchamiać i weryfikować aplikacje bezpośrednio w wybranym środowisku platformy Docker. Naciśnij klawisz F5, aby debugować aplikację (pojedynczy kontener lub wiele kontenerów) bezpośrednio na hoście platformy Docker, lub naciśnij klawisze Ctrl+F5, aby edytować i odświeżać aplikację bez konieczności odbudowywania kontenera. Jest to najprostszy i najpotężniejszy wybór dla deweloperów systemu Windows do tworzenia kontenerów Platformy Docker dla systemu Linux lub Windows.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio dla komputerów Mac (mac deweloper)

[Program Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) można używać podczas tworzenia aplikacji opartych na platformie Docker. Visual Studio dla komputerów Mac oferuje bogatsze IDE w porównaniu do programu Visual Studio Code for Mac.

## <a name="language-and-framework-choices"></a>Wybór języka i struktury

Aplikacje dokowania można tworzyć przy użyciu narzędzi firmy Microsoft w większości nowoczesnych języków. Poniżej znajduje się wstępna lista, ale nie ograniczasz się do niej:

- .NET Core i ASP.NET Core
- Node.js
- Przejdź
- Java
- Ruby
- Python

Zasadniczo można użyć dowolnego nowoczesnego języka obsługiwanego przez platformę Docker w systemie Linux lub Windows.

>[!div class="step-by-step"]
>[Poprzedni](deploy-azure-kubernetes-service.md)
>[następny](docker-apps-inner-loop-workflow.md)
