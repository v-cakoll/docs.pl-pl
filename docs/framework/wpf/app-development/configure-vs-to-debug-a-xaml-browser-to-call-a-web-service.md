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
ms.openlocfilehash: 182ceb96385bdca74d1d5c20079f78fe589982cf
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873206"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="c77b5-102">Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web</span><span class="sxs-lookup"><span data-stu-id="c77b5-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] <span data-ttu-id="c77b5-103">są uruchamiane w piaskownicy zabezpieczeń częściowego zaufania, który jest ograniczony do zestaw uprawnień strefy Internet.</span><span class="sxs-lookup"><span data-stu-id="c77b5-103"> run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="c77b5-104">Ten zestaw uprawnień ogranicza wywołania usługi sieci Web, aby tylko usług, które znajdują się w sieci Web [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikacji witryny pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="c77b5-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="c77b5-105">Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] debugowania z programu Visual Studio 2005, jednak nie wydaje się mieć tej samej lokacji, z którego pochodzą, sieci Web obsługi odwołań.</span><span class="sxs-lookup"><span data-stu-id="c77b5-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="c77b5-106">Wyjątki zabezpieczeń powoduje, że wywoływane, gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] próbuje wywołać usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c77b5-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="c77b5-107">Jednak program Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu można skonfigurować w celu symulowania o tej samej lokacji źródła jako usługę sieci Web wywoływanych przez nią podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="c77b5-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="c77b5-108">Dzięki temu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpiecznie wywołać usługę sieci Web bez powodowania wyjątki zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c77b5-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="c77b5-109">Konfigurowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c77b5-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="c77b5-110">Aby skonfigurować program Visual Studio 2005 do debugowania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] który wywołuje usługę sieci Web:</span><span class="sxs-lookup"><span data-stu-id="c77b5-110">To configure Visual Studio 2005 to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>

1.  <span data-ttu-id="c77b5-111">Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c77b5-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2.  <span data-ttu-id="c77b5-112">W **projektanta projektu**, kliknij przycisk **debugowania** kartę.</span><span class="sxs-lookup"><span data-stu-id="c77b5-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3.  <span data-ttu-id="c77b5-113">W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego** i wprowadź następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c77b5-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4.  <span data-ttu-id="c77b5-114">W **opcje uruchamiania** sekcji, wprowadź następujące informacje w **argumenty wiersza polecenia** pola tekstowego:</span><span class="sxs-lookup"><span data-stu-id="c77b5-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="c77b5-115">`-debug`  *Nazwa pliku*</span><span class="sxs-lookup"><span data-stu-id="c77b5-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="c77b5-116">*Filename* wartość **-debug** parametru jest nazwą pliku XBAP; na przykład:</span><span class="sxs-lookup"><span data-stu-id="c77b5-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
>  <span data-ttu-id="c77b5-117">Jest to domyślna konfiguracja dla rozwiązania, które są tworzone za pomocą programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="c77b5-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1.  <span data-ttu-id="c77b5-118">Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c77b5-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2.  <span data-ttu-id="c77b5-119">W **projektanta projektu**, kliknij przycisk **debugowania** kartę.</span><span class="sxs-lookup"><span data-stu-id="c77b5-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3.  <span data-ttu-id="c77b5-120">W **opcje uruchamiania** sekcji, Dodaj następujący parametr wiersza polecenia, aby **argumenty wiersza polecenia** pola tekstowego:</span><span class="sxs-lookup"><span data-stu-id="c77b5-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="c77b5-121">`-debugSecurityZoneURL`  *ADRES URL*</span><span class="sxs-lookup"><span data-stu-id="c77b5-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="c77b5-122">*Adresu URL* wartość **- debugSecurityZoneURL** parametr [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] lokalizacji, z którym chcesz przeprowadzić symulację jako witryna pochodzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c77b5-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="c77b5-123">Na przykład należy wziąć pod uwagę [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] używający usługi sieci Web z następującymi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="c77b5-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="c77b5-124">Witryna pochodzenia [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] dla tej sieci Web service to:</span><span class="sxs-lookup"><span data-stu-id="c77b5-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="c77b5-125">W związku z tym, pełne **- debugSecurityZoneURL** parametru wiersza polecenia, a wartość to:</span><span class="sxs-lookup"><span data-stu-id="c77b5-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="c77b5-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c77b5-126">See Also</span></span>
 [<span data-ttu-id="c77b5-127">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="c77b5-127">WPF Host (PresentationHost.exe)</span></span>](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
