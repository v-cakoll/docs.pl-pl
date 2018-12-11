---
title: Środowisko programistyczne dla aplikacji platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 471b52fd577e5560bd93e6da50f2032d63eb2e6f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152419"
---
# <a name="development-environment-for-docker-apps"></a>Środowisko programistyczne dla aplikacji platformy Docker

## <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzia do opracowywania: Środowiskiem IDE lub edytorem

Niezależnie od tego Jeśli wolisz, pełne i zaawansowanego środowiska IDE lub edytora lekkie i elastyczne, firma Microsoft ma potrzebne, jeśli chodzi o tworzenie aplikacji platformy Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code i interfejsu wiersza polecenia Docker (narzędzi dla wielu platform dla systemów Mac, Linux i Windows)

Jeśli wolisz lekkie Międzyplatformowe Edytor Obsługa dowolnego języka programowania, można użyć programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker. Te produkty zapewniają proste, ale niezawodne środowisko, co ma kluczowe znaczenie dla usprawnienie przepływu pracy dewelopera. Instalując "Docker for Mac" lub "Docker for Windows" (środowisko programistyczne), deweloperzy platformy Docker można użyć pojedynczego interfejsu wiersza polecenia platformy Docker do tworzenia aplikacji Windows lub Linux (środowisko uruchomieniowe). Ponadto w Visual Studio Code obsługuje rozszerzenia dla platformy Docker za pomocą funkcji IntelliSense dla plików Dockerfile i skrót zadania to uruchamianie poleceń Docker z poziomu edytora.

> [!NOTE]
> Aby pobrać program Visual Studio Code, przejdź do <https://code.visualstudio.com/download>.

Aby pobrać platformy Docker dla systemów Mac i Windows, przejdź do <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio z narzędziami Docker

Podczas korzystania z programu Visual Studio 2015 można zainstalować dodatkowe narzędzia "Narzędzia platformy Docker dla programu Visual Studio". Dla programu Visual Studio 2017 narzędzia platformy Docker są wbudowane już. W obu przypadkach można rozwijać, uruchamianie i Weryfikuj aplikacje bezpośrednio w wybranym środowisku platformy Docker. F5 aplikacji (jeden kontener lub wiele kontenerów) bezpośrednio do platformy Docker hosta debugowania lub naciśnij klawisze Ctrl + F5, aby edytować i odświeżać aplikację bez konieczności ponownego kompilowania kontenera. Jest to najprostsza i bardziej wydajne wyborem dla deweloperów Windows tworzenie kontenerów platformy Docker dla systemu Linux lub Windows.

> [!NOTE]
> Aby pobrać narzędzia aparatu Docker dla programu Visual Studio, przejdź do <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Opcje języka i struktury

Możesz opracowywać aplikacje platformy Docker i narzędzi firmy Microsoft przy użyciu najbardziej nowoczesnych języków. Poniżej przedstawiono listę początkowej, ale nie są ograniczone do niego:

-   .NET Core i ASP.NET Core
-   Node.js
-   Golang
-   Java
-   Ruby
-   Python

Zasadniczo można używać dowolnego języka modern, obsługiwane przez platformę Docker w systemie Linux lub Windows.

>[!div class="step-by-step"]
>[Poprzednie](orchestrate-high-scalability-availability.md)
>[dalej](docker-apps-inner-loop-workflow.md)