---
title: 'Instrukcje: Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: e41dd46e4ddbdcde6448c68b4f9fb2e073baca43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958687"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="cd77c-102">Instrukcje: Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej</span><span class="sxs-lookup"><span data-stu-id="cd77c-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="cd77c-103">Uruchom w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania ograniczonego do zestawu stref internetowych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="cd77c-103">run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="cd77c-104">Ten zestaw uprawnień ogranicza wywołania usługi sieci Web tylko do usług sieci Web, które znajdują [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] się w lokacji źródłowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd77c-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="cd77c-105">[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Gdy jest debugowany z programu Visual Studio 2005, chociaż nie jest uważany za taki sam, jak w przypadku usługi sieci Web, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="cd77c-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="cd77c-106">Powoduje to, że wyjątki zabezpieczeń zostaną zgłoszone [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] podczas próby wywołania usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cd77c-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="cd77c-107">Jednak projekt programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] można skonfigurować w taki sposób, aby symulacja była taka sama jak usługa sieci Web, która wywołuje podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="cd77c-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="cd77c-108">Pozwala [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to na bezpieczne Wywoływanie usługi sieci Web bez powodowania wyjątków zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cd77c-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="cd77c-109">Konfigurowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd77c-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="cd77c-110">Aby skonfigurować program Visual Studio 2005 do debugowania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , który wywołuje usługę sieci Web:</span><span class="sxs-lookup"><span data-stu-id="cd77c-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1. <span data-ttu-id="cd77c-111">Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cd77c-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="cd77c-112">W **projektancie projektu**kliknij kartę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="cd77c-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="cd77c-113">W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny** , a następnie wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="cd77c-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="cd77c-114">W sekcji **Opcje uruchamiania** wprowadź następujące polecenie w polu tekstowym **argumenty wiersza polecenia** :</span><span class="sxs-lookup"><span data-stu-id="cd77c-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="cd77c-115">`-debug`  *Nazwa pliku*</span><span class="sxs-lookup"><span data-stu-id="cd77c-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="cd77c-116">Wartość *filename* parametru **-Debug** to plik. XBAP. na przykład:</span><span class="sxs-lookup"><span data-stu-id="cd77c-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="cd77c-117">Jest to domyślna konfiguracja dla rozwiązań utworzonych przy użyciu szablonu projektu programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cd77c-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="cd77c-118">Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cd77c-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="cd77c-119">W **projektancie projektu**kliknij kartę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="cd77c-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="cd77c-120">W sekcji **Opcje uruchamiania** Dodaj następujący parametr wiersza polecenia do pola tekstowego **argumenty wiersza polecenia** :</span><span class="sxs-lookup"><span data-stu-id="cd77c-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="cd77c-121">`-debugSecurityZoneURL`  *ADRES URL*</span><span class="sxs-lookup"><span data-stu-id="cd77c-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="cd77c-122">Wartość *adresu URL* dla [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] parametru **-debugSecurityZoneURL** jest dla lokalizacji, która ma zostać symulowana jako witryna źródłowa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd77c-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="cd77c-123">Rozważmy na [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] przykład, że program korzysta z usługi sieci Web z następującymi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]czynnościami:</span><span class="sxs-lookup"><span data-stu-id="cd77c-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="cd77c-124">Lokacja pochodzenia [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] dla tej usługi sieci Web:</span><span class="sxs-lookup"><span data-stu-id="cd77c-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="cd77c-125">W związku z tym parametr wiersza polecenia Complete **-debugSecurityZoneURL** ma wartość:</span><span class="sxs-lookup"><span data-stu-id="cd77c-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="cd77c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd77c-126">See also</span></span>

- [<span data-ttu-id="cd77c-127">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="cd77c-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
