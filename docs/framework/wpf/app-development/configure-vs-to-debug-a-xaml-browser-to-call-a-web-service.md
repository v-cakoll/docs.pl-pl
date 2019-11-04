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
ms.openlocfilehash: 27319179a9a30c5693f47039bf1e24c59adf0e68
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424654"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="a520e-102">Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web</span><span class="sxs-lookup"><span data-stu-id="a520e-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
<span data-ttu-id="a520e-103">Aplikacje przeglądarki XAML (XBAP) działają w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania ograniczonego do zestawu stref internetowych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="a520e-103">XAML browser applications (XBAPs) run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="a520e-104">Ten zestaw uprawnień ogranicza wywołania usługi sieci Web tylko do usług sieci Web, które znajdują się w lokacji aplikacji XBAP.</span><span class="sxs-lookup"><span data-stu-id="a520e-104">This permission set restricts Web service calls to only Web services that are located at the XBAP application's site of origin.</span></span> <span data-ttu-id="a520e-105">Gdy XBAP jest debugowany z programu Visual Studio 2005, chociaż nie jest uważany za taki sam, jak w przypadku usługi sieci Web, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="a520e-105">When an XBAP is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="a520e-106">Powoduje to, że wyjątki zabezpieczeń mają być zgłaszane, gdy usługa XBAP próbuje wywołać usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a520e-106">This causes security exceptions to be raised when the XBAP attempts to call the Web service.</span></span> <span data-ttu-id="a520e-107">Jednak projekt programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] można skonfigurować w taki sposób, aby symulowany był taki sam, jak usługa sieci Web, która wywołuje podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="a520e-107">However, a Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="a520e-108">Umożliwia to aplikacji XBAP bezpieczne Wywoływanie usługi sieci Web bez powodowania wyjątków zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a520e-108">This allows the XBAP to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="a520e-109">Konfigurowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a520e-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="a520e-110">Aby skonfigurować program Visual Studio 2005 do debugowania aplikacji XBAP wywołującej usługę sieci Web:</span><span class="sxs-lookup"><span data-stu-id="a520e-110">To configure Visual Studio 2005 to debug an XBAP that calls a Web service:</span></span>

1. <span data-ttu-id="a520e-111">Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a520e-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="a520e-112">W **projektancie projektu**kliknij kartę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="a520e-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="a520e-113">W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny** , a następnie wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a520e-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="a520e-114">W sekcji **Opcje uruchamiania** wprowadź następujące polecenie w polu tekstowym **argumenty wiersza polecenia** :</span><span class="sxs-lookup"><span data-stu-id="a520e-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="a520e-115">*Nazwa pliku* `-debug`</span><span class="sxs-lookup"><span data-stu-id="a520e-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="a520e-116">Wartość *filename* parametru **-Debug** to plik. XBAP. na przykład:</span><span class="sxs-lookup"><span data-stu-id="a520e-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="a520e-117">Jest to domyślna konfiguracja dla rozwiązań utworzonych za pomocą szablonu projektu programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a520e-117">This is the default configuration for solutions that are created with the Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>

1. <span data-ttu-id="a520e-118">Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a520e-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="a520e-119">W **projektancie projektu**kliknij kartę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="a520e-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="a520e-120">W sekcji **Opcje uruchamiania** Dodaj następujący parametr wiersza polecenia do pola tekstowego **argumenty wiersza polecenia** :</span><span class="sxs-lookup"><span data-stu-id="a520e-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="a520e-121">*adres URL* `-debugSecurityZoneURL`</span><span class="sxs-lookup"><span data-stu-id="a520e-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="a520e-122">Wartość *adresu URL* dla parametru **-debugSecurityZoneURL** jest adresem URL lokalizacji, która ma być symulowana jako witryna pochodzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a520e-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the URL for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="a520e-123">Przykładowo Rozważmy aplikację przeglądarki XAML (XBAP), która używa usługi sieci Web z następującym adresem URL:</span><span class="sxs-lookup"><span data-stu-id="a520e-123">As an example, consider a XAML browser application (XBAP) that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="a520e-124">Witryna adresu URL źródła dla tej usługi sieci Web:</span><span class="sxs-lookup"><span data-stu-id="a520e-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="a520e-125">W związku z tym parametr wiersza polecenia Complete **-debugSecurityZoneURL** ma wartość:</span><span class="sxs-lookup"><span data-stu-id="a520e-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="a520e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a520e-126">See also</span></span>

- [<span data-ttu-id="a520e-127">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="a520e-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)
