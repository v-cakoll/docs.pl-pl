---
title: Host WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 586d306d0f375241c9382e1e24cf1af75b990ba9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122866"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="57ca4-102">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="57ca4-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="57ca4-103">Windows Presentation Foundation (WPF), hosta (PresentationHost.exe) to aplikacja, która umożliwia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje hostowane w przeglądarkach zgodne (w tym [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="57ca4-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="57ca4-104">Domyślnie Windows Presentation Foundation (WPF), hosta jest zarejestrowany jako powłoki i [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] Obsługa obsługiwane w przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartość, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="57ca4-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
-   <span data-ttu-id="57ca4-105">Luźne (nieskompilowanych) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików (.xaml).</span><span class="sxs-lookup"><span data-stu-id="57ca4-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="57ca4-106">(.xbap).</span><span class="sxs-lookup"><span data-stu-id="57ca4-106">(.xbap).</span></span>  
  
 <span data-ttu-id="57ca4-107">Pliki te typy hostów Windows Presentation Foundation (WPF):</span><span class="sxs-lookup"><span data-stu-id="57ca4-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
-   <span data-ttu-id="57ca4-108">Uruchamia zarejestrowaną [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] program obsługi, aby obsługiwać zawartość Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="57ca4-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
-   <span data-ttu-id="57ca4-109">Ładuje właściwych wersji wymaganego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] i zestawy Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="57ca4-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
-   <span data-ttu-id="57ca4-110">Gwarantuje, że zostały spełnione właściwe poziomy uprawnień dla strefy wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="57ca4-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="57ca4-111">W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="57ca4-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="57ca4-112">Użycie</span><span class="sxs-lookup"><span data-stu-id="57ca4-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="57ca4-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="57ca4-113">Parameters</span></span>  
  
|<span data-ttu-id="57ca4-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="57ca4-114">Parameter</span></span>|<span data-ttu-id="57ca4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="57ca4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57ca4-116">nazwa_pliku</span><span class="sxs-lookup"><span data-stu-id="57ca4-116">filename</span></span>|<span data-ttu-id="57ca4-117">Ścieżka pliku zostanie uaktywniony.</span><span class="sxs-lookup"><span data-stu-id="57ca4-117">The path of the file to be activated.</span></span> <span data-ttu-id="57ca4-118">Można też [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="57ca4-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="57ca4-119">-debug</span><span class="sxs-lookup"><span data-stu-id="57ca4-119">-debug</span></span>|<span data-ttu-id="57ca4-120">Podczas aktywowania aplikacji, nie Zatwierdź go do ani uruchomić go z magazynu.</span><span class="sxs-lookup"><span data-stu-id="57ca4-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="57ca4-121">Ta działa tylko wtedy, gdy plik lokalny jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="57ca4-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="57ca4-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="57ca4-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="57ca4-123">Używane z [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] wartości, aby wskazać PresentationHost.exe, że aplikację można debugować tak, jakby jego zostały wdrożone z określonego [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span><span class="sxs-lookup"><span data-stu-id="57ca4-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="57ca4-124">Określa strefę wdrożenia i witrynę pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="57ca4-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="57ca4-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="57ca4-125">-embedding</span></span>|<span data-ttu-id="57ca4-126">Wymagane przez OLE.</span><span class="sxs-lookup"><span data-stu-id="57ca4-126">Required by OLE.</span></span> <span data-ttu-id="57ca4-127">Jeśli `-event` lub `-debug` parametr jest określony, nie jest konieczne określić `-embedding` parametru, ponieważ ten parametr ma wartość wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="57ca4-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="57ca4-128">-Zdarzenie \<eventname ></span><span class="sxs-lookup"><span data-stu-id="57ca4-128">-event \<eventname></span></span>|<span data-ttu-id="57ca4-129">Otwórz zdarzenie o tej nazwie, a wyda sygnał, gdy PresentationHost.exe jest inicjowany i gotowe do hostowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="57ca4-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="57ca4-130">PresentationHost.exe przestaną obowiązywać w przypadku, gdy wystąpił błąd podczas otwierania zdarzenia, np. Jeśli go nie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="57ca4-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="57ca4-131">-launchApplication \<adresu url ></span><span class="sxs-lookup"><span data-stu-id="57ca4-131">-launchApplication \<url></span></span>|<span data-ttu-id="57ca4-132">Uruchamia autonomiczny [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji z określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="57ca4-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] <span data-ttu-id="57ca4-133">i są stosowane zasady zabezpieczeń WinINet dotyczących aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="57ca4-133">and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="57ca4-134">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="57ca4-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="57ca4-135">Obsługa powłoki</span><span class="sxs-lookup"><span data-stu-id="57ca4-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="57ca4-136">Program obsługi MIME</span><span class="sxs-lookup"><span data-stu-id="57ca4-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="57ca4-137">Visual Studio Debugging</span><span class="sxs-lookup"><span data-stu-id="57ca4-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="57ca4-138">Visual Studio Debugging In Zone</span><span class="sxs-lookup"><span data-stu-id="57ca4-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="57ca4-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57ca4-139">See also</span></span>

- [<span data-ttu-id="57ca4-140">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="57ca4-140">Security</span></span>](../security-wpf.md)
