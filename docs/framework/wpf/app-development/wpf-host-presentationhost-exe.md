---
title: Host WPF (PresentationHost.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b7662213d7204675de7e8681b6fc8141f04dd21
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="747d9-102">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="747d9-102">WPF Host (PresentationHost.exe)</span></span>
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]<span data-ttu-id="747d9-103">Host (PresentationHost.exe) to aplikacja, która umożliwia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji ma być obsługiwana w przeglądarkach zgodne (w tym [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] i nowsze).</span><span class="sxs-lookup"><span data-stu-id="747d9-103"> Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="747d9-104">Domyślnie [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] hosta jest zarejestrowany jako powłoki i [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] Obsługa oparta na przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartość, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="747d9-104">By default, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
-   <span data-ttu-id="747d9-105">Luźne (nieskompilowanych) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików (.xaml).</span><span class="sxs-lookup"><span data-stu-id="747d9-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]<span data-ttu-id="747d9-106">(.xbap).</span><span class="sxs-lookup"><span data-stu-id="747d9-106"> (.xbap).</span></span>  
  
 <span data-ttu-id="747d9-107">Pliki te typy [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] hosta:</span><span class="sxs-lookup"><span data-stu-id="747d9-107">For files of these types, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host:</span></span>  
  
-   <span data-ttu-id="747d9-108">Uruchamia zarejestrowaną [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] obsługi hosta [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="747d9-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] content.</span></span>  
  
-   <span data-ttu-id="747d9-109">Ładuje właściwych wersji wymaganego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] i [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="747d9-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] assemblies.</span></span>  
  
-   <span data-ttu-id="747d9-110">Gwarantuje, że poziomy odpowiednich uprawnień dla strefy wdrożenia zostały spełnione.</span><span class="sxs-lookup"><span data-stu-id="747d9-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="747d9-111">W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="747d9-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="747d9-112">Użycie</span><span class="sxs-lookup"><span data-stu-id="747d9-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="747d9-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="747d9-113">Parameters</span></span>  
  
|<span data-ttu-id="747d9-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="747d9-114">Parameter</span></span>|<span data-ttu-id="747d9-115">Opis</span><span class="sxs-lookup"><span data-stu-id="747d9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="747d9-116">nazwa_pliku</span><span class="sxs-lookup"><span data-stu-id="747d9-116">filename</span></span>|<span data-ttu-id="747d9-117">Ścieżka pliku do aktywacji.</span><span class="sxs-lookup"><span data-stu-id="747d9-117">The path of the file to be activated.</span></span> <span data-ttu-id="747d9-118">Można też [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="747d9-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="747d9-119">-debug</span><span class="sxs-lookup"><span data-stu-id="747d9-119">-debug</span></span>|<span data-ttu-id="747d9-120">Podczas aktywacji aplikacji, nie go do zatwierdzenia lub uruchomić go z magazynu.</span><span class="sxs-lookup"><span data-stu-id="747d9-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="747d9-121">Ta działa tylko wtedy, gdy plik lokalny jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="747d9-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="747d9-122">-debugSecurityZoneURL \<adres url ></span><span class="sxs-lookup"><span data-stu-id="747d9-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="747d9-123">Używane z [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] wartości wskazującej PresentationHost.exe, że aplikację można debugować tak, jakby były na nim wdrożone z określonego [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span><span class="sxs-lookup"><span data-stu-id="747d9-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="747d9-124">Określa zarówno strefy wdrażania, jak i witryny pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="747d9-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="747d9-125">-Osadzanie</span><span class="sxs-lookup"><span data-stu-id="747d9-125">-embedding</span></span>|<span data-ttu-id="747d9-126">Wymagane przez OLE.</span><span class="sxs-lookup"><span data-stu-id="747d9-126">Required by OLE.</span></span> <span data-ttu-id="747d9-127">Jeśli `-event` lub `-debug` podano parametr nie jest konieczne w celu określenia `-embedding` parametru, ponieważ ten parametr ma wartość wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="747d9-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="747d9-128">-zdarzeń \<eventname ></span><span class="sxs-lookup"><span data-stu-id="747d9-128">-event \<eventname></span></span>|<span data-ttu-id="747d9-129">Otworzyć zdarzenia o tej nazwie i sygnału go, gdy PresentationHost.exe jest zainicjowana i gotowa do hosta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="747d9-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="747d9-130">PresentationHost.exe spowoduje przerwanie Jeśli wystąpił błąd podczas otwierania zdarzenia, np. Jeśli go nie już został utworzony.</span><span class="sxs-lookup"><span data-stu-id="747d9-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="747d9-131">-launchApplication \<adres url ></span><span class="sxs-lookup"><span data-stu-id="747d9-131">-launchApplication \<url></span></span>|<span data-ttu-id="747d9-132">Uruchamia autonomiczny [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji z podanego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="747d9-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]<span data-ttu-id="747d9-133">i są stosowane zasady zabezpieczeń WinINet dotyczących aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="747d9-133"> and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="747d9-134">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="747d9-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="747d9-135">Obsługa powłoki</span><span class="sxs-lookup"><span data-stu-id="747d9-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="747d9-136">Program obsługi MIME</span><span class="sxs-lookup"><span data-stu-id="747d9-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="747d9-137">Debugowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="747d9-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="747d9-138">Visual Studio debugowanie w strefie</span><span class="sxs-lookup"><span data-stu-id="747d9-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="747d9-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="747d9-139">See Also</span></span>  
 [<span data-ttu-id="747d9-140">Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="747d9-140">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
