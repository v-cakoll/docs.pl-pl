---
title: Host WPF (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743403"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="52bf3-102">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="52bf3-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="52bf3-103">Windows Presentation Foundation (WPF) Host (PresentationHost. exe) to aplikacja, która umożliwia obsługiwanie aplikacji WPF w zgodnych przeglądarkach (w tym programu Microsoft Internet Explorer 6 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="52bf3-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="52bf3-104">Domyślnie Host Windows Presentation Foundation (WPF) jest zarejestrowany jako powłoka i obsługa MIME dla zawartości WPF hostowanej w przeglądarce, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="52bf3-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="52bf3-105">Luźno (niekompilowane) pliki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (. XAML).</span><span class="sxs-lookup"><span data-stu-id="52bf3-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="52bf3-106">Aplikacja przeglądarki XAML (XBAP) (XBAP).</span><span class="sxs-lookup"><span data-stu-id="52bf3-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="52bf3-107">Dla plików tego typu Windows Presentation Foundation (WPF) Host:</span><span class="sxs-lookup"><span data-stu-id="52bf3-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="52bf3-108">Uruchamia zarejestrowaną procedurę obsługi HTML do hostowania zawartości Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="52bf3-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="52bf3-109">Ładuje odpowiednie wersje zestawów wymaganych przez środowisko uruchomieniowe języka wspólnego (CLR) i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="52bf3-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="52bf3-110">Zapewnia, że stosowane są odpowiednie poziomy uprawnień dla strefy wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="52bf3-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="52bf3-111">W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="52bf3-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="52bf3-112">Użycie</span><span class="sxs-lookup"><span data-stu-id="52bf3-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="52bf3-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="52bf3-113">Parameters</span></span>  
  
|<span data-ttu-id="52bf3-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="52bf3-114">Parameter</span></span>|<span data-ttu-id="52bf3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="52bf3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52bf3-116">nazwa_pliku</span><span class="sxs-lookup"><span data-stu-id="52bf3-116">filename</span></span>|<span data-ttu-id="52bf3-117">Ścieżka pliku, który ma zostać aktywowany.</span><span class="sxs-lookup"><span data-stu-id="52bf3-117">The path of the file to be activated.</span></span> <span data-ttu-id="52bf3-118">Może również być identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="52bf3-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="52bf3-119">-debug</span><span class="sxs-lookup"><span data-stu-id="52bf3-119">-debug</span></span>|<span data-ttu-id="52bf3-120">Podczas aktywowania aplikacji program nie zatwierdza jej ani nie uruchamia ze sklepu.</span><span class="sxs-lookup"><span data-stu-id="52bf3-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="52bf3-121">Działa to tylko wtedy, gdy plik lokalny jest aktywowany.</span><span class="sxs-lookup"><span data-stu-id="52bf3-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="52bf3-122">-debugSecurityZoneURL \<adres URL ></span><span class="sxs-lookup"><span data-stu-id="52bf3-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="52bf3-123">Używany z wartością adresu URL, aby wskazać PresentationHost. exe, że aplikacja powinna być debugowana tak, jakby została wdrożona z określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="52bf3-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="52bf3-124">Określa strefę wdrożenia i lokację źródłową.</span><span class="sxs-lookup"><span data-stu-id="52bf3-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="52bf3-125">— Osadzanie</span><span class="sxs-lookup"><span data-stu-id="52bf3-125">-embedding</span></span>|<span data-ttu-id="52bf3-126">Wymagane przez OLE.</span><span class="sxs-lookup"><span data-stu-id="52bf3-126">Required by OLE.</span></span> <span data-ttu-id="52bf3-127">Jeśli parametr `-event` lub `-debug` jest określony, nie trzeba określać `-embedding` parametru, ponieważ ten parametr jest ustawiony wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="52bf3-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="52bf3-128">-Event \<EventName ></span><span class="sxs-lookup"><span data-stu-id="52bf3-128">-event \<eventname></span></span>|<span data-ttu-id="52bf3-129">Otwórz zdarzenie o tej nazwie i sygnalizuj go, gdy PresentationHost. exe zostanie zainicjowany i będzie gotowy do hostowania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="52bf3-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="52bf3-130">PresentationHost. exe zakończy się, jeśli wystąpił błąd podczas otwierania zdarzenia, na przykład jeśli nie został jeszcze utworzony.</span><span class="sxs-lookup"><span data-stu-id="52bf3-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="52bf3-131">-launchApplication \<adres URL ></span><span class="sxs-lookup"><span data-stu-id="52bf3-131">-launchApplication \<url></span></span>|<span data-ttu-id="52bf3-132">Uruchamia autonomiczną aplikację ClickOnce z podanego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="52bf3-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="52bf3-133">Stosowane są zasady zabezpieczeń programu Internet Explorer i WinINet dotyczące aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="52bf3-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="52bf3-134">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="52bf3-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="52bf3-135">Procedura obsługi powłoki</span><span class="sxs-lookup"><span data-stu-id="52bf3-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="52bf3-136">Procedura obsługi MIME</span><span class="sxs-lookup"><span data-stu-id="52bf3-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="52bf3-137">Debugowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="52bf3-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="52bf3-138">Debugowanie programu Visual Studio w strefie</span><span class="sxs-lookup"><span data-stu-id="52bf3-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="52bf3-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52bf3-139">See also</span></span>

- [<span data-ttu-id="52bf3-140">Security</span><span class="sxs-lookup"><span data-stu-id="52bf3-140">Security</span></span>](../security-wpf.md)
