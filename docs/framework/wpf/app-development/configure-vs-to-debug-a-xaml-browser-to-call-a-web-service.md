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
ms.openlocfilehash: 948a730185650cb3449202503a049e9caff7c4bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547503"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="4a9d1-102">Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web</span><span class="sxs-lookup"><span data-stu-id="4a9d1-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="4a9d1-103"> Uruchom w piaskownicy zabezpieczenia częściowego zaufania, który jest ograniczony do strefy Internet zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-103"> run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="4a9d1-104">Ten zestaw uprawnień ogranicza wywołania usługi sieci Web tylko usługi, które znajdują się w sieci Web [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikacji witryny pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="4a9d1-105">Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] debugowania z [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], ale uznano nie mają tej samej witrynie pochodzenia, zgodnie z sieci Web usługi odwołania.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="4a9d1-106">Wyjątki zabezpieczeń powoduje, że wygenerowany, gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] próby wywołania usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="4a9d1-107">Jednak [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu można skonfigurować w celu symulowania o tej samej lokacji pochodzenia jako usługę sieci Web wywołuje podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-107">However, a [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="4a9d1-108">Dzięki temu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpiecznie wywołać usługę sieci Web bez powodowania wyjątki zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>  
  
## <a name="configuring-visual-studio"></a><span data-ttu-id="4a9d1-109">Konfigurowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4a9d1-109">Configuring Visual Studio</span></span>  
 <span data-ttu-id="4a9d1-110">Aby skonfigurować [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] debugowania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] wywołującym usługi sieci Web:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-110">To configure [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>  
  
1.  <span data-ttu-id="4a9d1-111">Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4a9d1-112">W **projektanta projektu**, kliknij przycisk **debugowania** kartę.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-112">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="4a9d1-113">W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego** i wprowadź następujące:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  <span data-ttu-id="4a9d1-114">W **opcje uruchamiania** wprowadź poniższy **argumenty wiersza polecenia** pole tekstowe:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="4a9d1-115">`-debug`  *Nazwa pliku*</span><span class="sxs-lookup"><span data-stu-id="4a9d1-115">`-debug`  *filename*</span></span>  
  
     <span data-ttu-id="4a9d1-116">*Filename* wartość **-debug** parametru jest nazwa pliku .xbap, np.:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  <span data-ttu-id="4a9d1-117">Jest to konfiguracja domyślna rozwiązań, które zostały utworzone z [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-117">This is the default configuration for solutions that are created with the [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>  
  
1.  <span data-ttu-id="4a9d1-118">Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4a9d1-119">W **projektanta projektu**, kliknij przycisk **debugowania** kartę.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-119">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="4a9d1-120">W **opcje uruchamiania** Dodaj następujący parametr wiersza polecenia do **argumenty wiersza polecenia** pole tekstowe:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="4a9d1-121">`-debugSecurityZoneURL`  *ADRES URL*</span><span class="sxs-lookup"><span data-stu-id="4a9d1-121">`-debugSecurityZoneURL`  *URL*</span></span>  
  
     <span data-ttu-id="4a9d1-122">*Adres URL* wartość **- debugSecurityZoneURL** jest parametr [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] dla lokalizacji, w której chcesz symulować jako witryny pochodzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>  
  
 <span data-ttu-id="4a9d1-123">Na przykład należy wziąć pod uwagę [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] używającą usługi sieci Web z następującymi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 <span data-ttu-id="4a9d1-124">Witryny pochodzenia [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] dla tej witryny sieci Web service jest:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>  
  
 `http://services.msdn.microsoft.com`  
  
 <span data-ttu-id="4a9d1-125">W rezultacie pełną **- debugSecurityZoneURL** parametru wiersza polecenia, a wartość to:</span><span class="sxs-lookup"><span data-stu-id="4a9d1-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a><span data-ttu-id="4a9d1-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a9d1-126">See Also</span></span>  
 [<span data-ttu-id="4a9d1-127">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="4a9d1-127">WPF Host (PresentationHost.exe)</span></span>](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
