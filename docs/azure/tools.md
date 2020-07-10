---
title: Narzędzia dla deweloperów platformy Azure
description: Pobierz narzędzia, aby rozpocząć korzystanie z bibliotek platformy Azure .NET ze środowiska systemów Windows, Linux i Mac.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174954"
---
# <a name="azure-tools-for-developing-with-net"></a>Narzędzia platformy Azure do programowania przy użyciu platformy .NET

## <a name="sdk-downloads"></a>Pliki do pobrania zestawu SDK

Biblioteki platformy Azure dla platformy .NET są implementowane jako [pakiety NuGet](https://www.nuget.org/packages?q=windowsazureofficial). Zobacz dokumentację [interfejsu API](/dotnet/api/overview/azure/?view=azure-dotnet) , aby zapoznać się z dokumentacją referencyjną uporządkowaną według usługi platformy Azure.

## <a name="development-tools"></a>Narzędzia programistyczne

Program Visual Studio zawiera narzędzia dla wielu wbudowanych usług platformy Azure. Niektóre usługi platformy Azure mają dostępne dodatkowe narzędzia lub emulatory, takie jak [Eksplorator usługi Azure Storage](https://azure.microsoft.com/features/storage-explorer/). W razie potrzeby zapoznaj się z dokumentacją usługi platformy Azure.

Wybierz odpowiednie środowisko programistyczne poniżej.

## <a name="visual-studio-on-windows"></a>[Program Visual Studio w systemie Windows](#tab/vs)

Program Visual Studio w wersji 2017 lub nowszej ma wbudowaną obsługę programowania na platformie Azure. Poniższe kroki opisują włączenie obsługi projektowania platformy Azure w programie Visual Studio.

W przypadku programu Visual Studio 2015 i wcześniejszych należy <a href="vs2015-install.md">wykonać te instrukcje</a>.

### <a name="step-1-download-visual-studio-2019"></a>Krok 1. Pobieranie programu Visual Studio 2019

Możesz pominąć ten krok, jeśli masz już zainstalowany program Visual Studio 2019.

> [!div class="nextstepaction"]
> [Pobierz program Visual Studio 2019](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>Krok 2. Instalowanie dwóch obciążeń platformy Azure

W Instalatorze programu Visual Studio Zainstaluj program Visual Studio (lub zmodyfikuj istniejącą instalację). Upewnij się, że wybrano obciążenia na *platformie Azure* i *ASP.NET i programowanie dla sieci Web* .

### <a name="step-3-develop-with-net-on-azure"></a>Krok 3. Programowanie przy użyciu platformy .NET na platformie Azure

Zacznij od [wdrożenia pierwszej ASP.NET Core aplikacji sieci Web na Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).

## <a name="visual-studio-code-cross-platform"></a>[Visual Studio Code (wiele platform)](#tab/vscode)

Visual Studio Code ma wszystko, czego potrzebujesz do tworzenia aplikacji dla wielu platform na platformie Azure.

### <a name="step-1-download-the-net-core-sdk"></a>Krok 1. Pobieranie zestaw .NET Core SDK

Zestaw SDK i narzędzia wiersza polecenia dla aplikacji platformy .NET Core.

> [!div class="nextstepaction"]
> [Pobierz zestaw .NET Core SDK](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>Krok 2. Visual Studio Code

Edytuj i Debuguj aplikacje platformy .NET Core w dowolnym systemie operacyjnym: Windows, Mac i Linux.

> [!div class="nextstepaction"]
> [Pobierz Visual Studio Code](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a>Krok 3. rozszerzenie narzędzi platformy Azure

Zainstaluj rozszerzenie narzędzi platformy Azure w Visual Studio Code.

> [!div class="nextstepaction"]
> [Zainstaluj rozszerzenie narzędzi platformy Azure](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a>Krok 4. Programowanie przy użyciu platformy .NET na platformie Azure

Zacznij od [wdrożenia pierwszej ASP.NET Core aplikacji sieci Web na Azure App Service w systemie Linux](/azure/app-service/containers/quickstart-dotnetcore).

---
