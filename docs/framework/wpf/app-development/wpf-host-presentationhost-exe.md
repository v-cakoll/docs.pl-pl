---
title: Host WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 981e518a55f179c2fbf44534783c80fb230e4ecf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421124"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="a5a1b-102">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="a5a1b-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="a5a1b-103">Windows Presentation Foundation (WPF) Host (PresentationHost. exe) to aplikacja, która umożliwia obsługiwanie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji w zgodnych przeglądarkach (w tym programu Microsoft Internet Explorer 6 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="a5a1b-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="a5a1b-104">Domyślnie Host Windows Presentation Foundation (WPF) jest zarejestrowany jako powłoka i obsługa MIME dla zawartości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostowanej w przeglądarce, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="a5a1b-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="a5a1b-105">Luźno (niekompilowane) pliki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (. XAML).</span><span class="sxs-lookup"><span data-stu-id="a5a1b-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="a5a1b-106">Aplikacja przeglądarki XAML (XBAP) (XBAP).</span><span class="sxs-lookup"><span data-stu-id="a5a1b-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="a5a1b-107">Dla plików tego typu Windows Presentation Foundation (WPF) Host:</span><span class="sxs-lookup"><span data-stu-id="a5a1b-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="a5a1b-108">Uruchamia zarejestrowaną procedurę obsługi HTML do hostowania zawartości Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a5a1b-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="a5a1b-109">Ładuje odpowiednie wersje zestawów wymaganych przez środowisko uruchomieniowe języka wspólnego (CLR) i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a5a1b-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="a5a1b-110">Zapewnia, że stosowane są odpowiednie poziomy uprawnień dla strefy wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="a5a1b-111">W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="a5a1b-112">Użycie</span><span class="sxs-lookup"><span data-stu-id="a5a1b-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="a5a1b-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5a1b-113">Parameters</span></span>  
  
|<span data-ttu-id="a5a1b-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="a5a1b-114">Parameter</span></span>|<span data-ttu-id="a5a1b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a5a1b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5a1b-116">nazwa_pliku</span><span class="sxs-lookup"><span data-stu-id="a5a1b-116">filename</span></span>|<span data-ttu-id="a5a1b-117">Ścieżka pliku, który ma zostać aktywowany.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-117">The path of the file to be activated.</span></span> <span data-ttu-id="a5a1b-118">Może również być identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="a5a1b-119">-debug</span><span class="sxs-lookup"><span data-stu-id="a5a1b-119">-debug</span></span>|<span data-ttu-id="a5a1b-120">Podczas aktywowania aplikacji program nie zatwierdza jej ani nie uruchamia ze sklepu.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="a5a1b-121">Działa to tylko wtedy, gdy plik lokalny jest aktywowany.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="a5a1b-122">-debugSecurityZoneURL \<url ></span><span class="sxs-lookup"><span data-stu-id="a5a1b-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="a5a1b-123">Używany z wartością adresu URL, aby wskazać PresentationHost. exe, że aplikacja powinna być debugowana tak, jakby została wdrożona z określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="a5a1b-124">Określa strefę wdrożenia i lokację źródłową.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="a5a1b-125">— Osadzanie</span><span class="sxs-lookup"><span data-stu-id="a5a1b-125">-embedding</span></span>|<span data-ttu-id="a5a1b-126">Wymagane przez OLE.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-126">Required by OLE.</span></span> <span data-ttu-id="a5a1b-127">Jeśli określono parametr `-event` lub `-debug`, nie trzeba określać `-embedding` parametru, ponieważ ten parametr jest ustawiony wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="a5a1b-128">-\<eventname zdarzeń ></span><span class="sxs-lookup"><span data-stu-id="a5a1b-128">-event \<eventname></span></span>|<span data-ttu-id="a5a1b-129">Otwórz zdarzenie o tej nazwie i sygnalizuj go, gdy PresentationHost. exe zostanie zainicjowany i będzie gotowy do hostowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="a5a1b-130">PresentationHost. exe zakończy się, jeśli wystąpił błąd podczas otwierania zdarzenia, na przykład jeśli nie został jeszcze utworzony.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="a5a1b-131">-launchApplication \<url ></span><span class="sxs-lookup"><span data-stu-id="a5a1b-131">-launchApplication \<url></span></span>|<span data-ttu-id="a5a1b-132">Uruchamia autonomiczną aplikację ClickOnce z podanego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="a5a1b-133">Stosowane są zasady zabezpieczeń programu Internet Explorer i WinINet dotyczące aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="a5a1b-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="a5a1b-134">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="a5a1b-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="a5a1b-135">Procedura obsługi powłoki</span><span class="sxs-lookup"><span data-stu-id="a5a1b-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="a5a1b-136">Procedura obsługi MIME</span><span class="sxs-lookup"><span data-stu-id="a5a1b-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="a5a1b-137">Debugowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a5a1b-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="a5a1b-138">Debugowanie programu Visual Studio w strefie</span><span class="sxs-lookup"><span data-stu-id="a5a1b-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="a5a1b-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5a1b-139">See also</span></span>

- [<span data-ttu-id="a5a1b-140">Security</span><span class="sxs-lookup"><span data-stu-id="a5a1b-140">Security</span></span>](../security-wpf.md)
