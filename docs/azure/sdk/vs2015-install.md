---
title: Narzędzia platformy Azure dla programu Visual Studio 2015
description: Pobierz narzędzia, aby rozpocząć korzystanie z bibliotek platformy Azure .NET z programu Visual Studio 2015.
ms.date: 10/19/2017
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: a29709d56f2debe04d49ee4eafdc27acd4ca480f
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071928"
---
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="18389-103">Narzędzia platformy Azure dla programu Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="18389-103">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="18389-104">Najszybszym i najprostszym sposobem instalowania **zestawu Azure SDK dla programu Visual studio 2015** i **Service Fabric SDK oraz narzędzi dla programu Visual Studio 2015** jest użycie [Instalatora platformy sieci Web](https://www.microsoft.com/web/downloads/platform.aspx).</span><span class="sxs-lookup"><span data-stu-id="18389-104">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span> <span data-ttu-id="18389-105">Instalator platformy Microsoft Web to bezpłatne narzędzie usprawniające pobieranie, Instalowanie i aktualizowanie niektórych składników platformy sieci Web firmy Microsoft, w tym narzędzi platformy Azure dla programu Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="18389-105">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span> <span data-ttu-id="18389-106">Te zestawy SDK można także pobrać i zainstalować jako pojedyncze składniki ze [strony plików do pobrania platformy Azure](https://azure.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="18389-106">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span>

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="18389-107">Korzystanie z Instalatora platformy sieci Web</span><span class="sxs-lookup"><span data-stu-id="18389-107">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="18389-108">Pobierz i uruchom program [inicjujący Instalatora platformy sieci Web](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span><span class="sxs-lookup"><span data-stu-id="18389-108">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>

2. <span data-ttu-id="18389-109">Program inicjujący zainstaluje Instalatora platformy sieci Web (w razie potrzeby) i automatycznie umieści najnowsze wersje **zestawu Azure SDK dla programu Visual studio 2015** oraz **Service Fabric zestaw SDK i narzędzia dla programu Visual Studio 2015** elementy na liście *elementów do zainstalowania* .</span><span class="sxs-lookup"><span data-stu-id="18389-109">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span> <span data-ttu-id="18389-110">Kliknij przycisk **Instaluj**.</span><span class="sxs-lookup"><span data-stu-id="18389-110">Click **Install**.</span></span>

    ![Instalator platformy sieci Web](../media/sdk/vs2015-install/webpi.png)

3. <span data-ttu-id="18389-112">Na następnym ekranie kliknij pozycję **Akceptuję**.</span><span class="sxs-lookup"><span data-stu-id="18389-112">On the next screen, click **I Accept**.</span></span> <span data-ttu-id="18389-113">W sieci Web PI rozpocznie się pobieranie i Instalowanie wybranych składników.</span><span class="sxs-lookup"><span data-stu-id="18389-113">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="18389-114">Po zakończeniu instalacji zostanie wyświetlony ekran potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="18389-114">After the installation is finished, it will display a confirmation screen.</span></span> <span data-ttu-id="18389-115">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="18389-115">Click **Finish**.</span></span> <span data-ttu-id="18389-116">Możesz teraz zamknąć Instalatora platformy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="18389-116">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="18389-117">Weryfikowanie instalacji</span><span class="sxs-lookup"><span data-stu-id="18389-117">Verifying the installation</span></span>

1. <span data-ttu-id="18389-118">W programie Visual Studio 2015 kliknij menu **Narzędzia** , a następnie kliknij pozycję **rozszerzenia i aktualizacje..**..</span><span class="sxs-lookup"><span data-stu-id="18389-118">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="18389-119">Wyświetlana lista będzie zawierać kilka narzędzi platformy Azure, takich jak **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**i **Service Fabric Tools**.</span><span class="sxs-lookup"><span data-stu-id="18389-119">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![Rozszerzenia i aktualizacje](../media/sdk/vs2015-install/ext-tools.png)
