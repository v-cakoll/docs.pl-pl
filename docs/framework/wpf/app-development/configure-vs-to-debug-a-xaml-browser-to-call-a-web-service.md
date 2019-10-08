---
title: Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 8ec278f2bc66d9b40786123af684f6468b6a9d83
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005673"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="5434e-102">Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web</span><span class="sxs-lookup"><span data-stu-id="5434e-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] <span data-ttu-id="5434e-103">przebiega w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania ograniczonego do zestawu stref internetowych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="5434e-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="5434e-104">Ten zestaw uprawnień ogranicza wywołania usługi sieci Web tylko do usług sieci Web, które znajdują się w lokacji "[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]" aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5434e-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="5434e-105">Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] jest debugowana z programu Visual Studio 2005, chociaż nie jest uważany za ma tę samą lokację pochodzenia jak usługa sieci Web, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="5434e-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="5434e-106">Powoduje to wystąpienie wyjątków zabezpieczeń, gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] próbuje wywołać usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5434e-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="5434e-107">Jednak projekt programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] można skonfigurować w taki sposób, aby symuluje istnienie tej samej lokacji pochodzenia jak usługa sieci Web, która wywołuje podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="5434e-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="5434e-108">Umożliwia to [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpieczne Wywoływanie usługi sieci Web bez powodowania wyjątków zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5434e-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="5434e-109">Konfigurowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5434e-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="5434e-110">Aby skonfigurować program Visual Studio 2005 do debugowania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], który wywołuje usługę sieci Web:</span><span class="sxs-lookup"><span data-stu-id="5434e-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="5434e-111">Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5434e-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="5434e-112">W **projektancie projektu**kliknij kartę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="5434e-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="5434e-113">W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny** , a następnie wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5434e-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="5434e-114">W sekcji **Opcje uruchamiania** wprowadź następujące polecenie w polu tekstowym **argumenty wiersza polecenia** :</span><span class="sxs-lookup"><span data-stu-id="5434e-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="5434e-115">*Nazwa pliku* `-debug`</span><span class="sxs-lookup"><span data-stu-id="5434e-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="5434e-116">Wartość *filename* parametru **-Debug** to plik. XBAP. na przykład:</span><span class="sxs-lookup"><span data-stu-id="5434e-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="5434e-117">Jest to domyślna konfiguracja dla rozwiązań utworzonych za pomocą szablonu projektu programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5434e-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="5434e-118">Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5434e-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="5434e-119">W **projektancie projektu**kliknij kartę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="5434e-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="5434e-120">W sekcji **Opcje uruchamiania** Dodaj następujący parametr wiersza polecenia do pola tekstowego **argumenty wiersza polecenia** :</span><span class="sxs-lookup"><span data-stu-id="5434e-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="5434e-121">*adres URL* `-debugSecurityZoneURL`</span><span class="sxs-lookup"><span data-stu-id="5434e-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="5434e-122">Wartość *adresu URL* dla parametru **-debugSecurityZoneURL** jest [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] dla lokalizacji, która ma zostać symulowana jako witryna pochodzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5434e-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="5434e-123">Na przykład rozważmy [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], który używa usługi sieci Web z następującym adresem URL:</span><span class="sxs-lookup"><span data-stu-id="5434e-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="5434e-124">Witryna adresu URL źródła dla tej usługi sieci Web:</span><span class="sxs-lookup"><span data-stu-id="5434e-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="5434e-125">W związku z tym parametr wiersza polecenia Complete **-debugSecurityZoneURL** ma wartość:</span><span class="sxs-lookup"><span data-stu-id="5434e-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="5434e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5434e-126">See also</span></span>

- [<span data-ttu-id="5434e-127">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="5434e-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
