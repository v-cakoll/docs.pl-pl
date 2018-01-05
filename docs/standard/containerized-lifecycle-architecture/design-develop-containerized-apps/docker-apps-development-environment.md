---
title: "Środowisko projektowe dla aplikacji Docker"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad1a6e4cb0974ebb067cf1a7be987d696e8bc82a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="development-environment-for-docker-apps"></a>Środowisko projektowe dla aplikacji Docker

## <a name="development-tools-choices-ide-or-editor"></a>Opcje narzędzi programistycznych: IDE lub edytora

Niezależnie Jeśli wolisz pełne i wydajne środowiska IDE lub edytora nieskomplikowane i elastyczne, firma Microsoft ma będzie po przejściu tworzenia aplikacji Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code i Docker interfejsu wiersza polecenia (narzędzia wieloplatformowe dla komputerów Mac, Linux i Windows)

Jeśli wolisz edytorze niewielka, między platformami obsługi żadnego języka programowania, można użyć programu Visual Studio Code i interfejsu wiersza polecenia Docker. Te produkty zapewniają proste, ale niezawodne środowisko, co jest szczególnie ważne dla usprawnienie przepływu pracy deweloperów. Instalując "Docker dla komputerów Mac" lub "Docker dla systemu Windows" (development environment), Docker deweloperzy mogą używać jednego interfejsu wiersza polecenia Docker, aby tworzyć aplikacje systemu Windows lub Linux (środowisko uruchomieniowe). Ponadto w Visual Studio Code obsługuje rozszerzenia dla Docker z technologii IntelliSense dla Dockerfiles oraz skrót zadania Docker poleceń w edytorze.

> [!NOTE]
> Aby pobrać program Visual Studio Code, przejdź do <https://code.visualstudio.com/download>.

Aby pobrać Docker dla systemów Mac i systemu Windows, przejdź do <http://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Program Visual Studio z narzędziami Docker

Podczas korzystania z programu Visual Studio 2015 można zainstalować dodatkowe narzędzia "Docker Tools for Visual Studio". Dla programu Visual Studio 2017 r narzędzia Docker są wbudowane już. W obu przypadkach można rozwijać, uruchamiania i sprawdzanie poprawności aplikacji bezpośrednio w wybranym środowisku Docker. F5 aplikacji (jeden kontener lub wielu kontenerów) bezpośrednio do Docker hosta z debugowaniem, lub naciśnij klawisze Ctrl + F5, edytowanie i odświeżanie aplikacji bez konieczności odbudować kontenera. Jest to najprostsza i bardziej wydajne wybór dla deweloperów systemu Windows, tworzenie kontenerów Docker dla systemu Linux lub Windows.

> [!NOTE]
> Aby pobrać narzędzia Docker dla programu Visual Studio, przejdź do <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Opcje języka i framework

Można programować aplikacje Docker i narzędzi firmy Microsoft z większość nowoczesnych języków. Poniżej przedstawiono listę początkowej, ale nie są ograniczone do niej:

-   Oprogramowanie .NET core i ASP.NET Core

-   Node.js

-   Golang

-   Java

-   Ruby

-   Python

Zasadniczo można użyć dowolnego nowoczesnych języków obsługiwanych przez Docker w systemie Linux lub Windows.


>[!div class="step-by-step"]
[Poprzednie] (organizowania wysoki skalowalność availability.md) [dalej] (docker aplikacje — wewnętrzny pętli workflow.md)
