---
title: Host WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 64ba1261134184f22e9faf157ca70e3471e3b3cb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636253"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="d305c-102">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="d305c-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="d305c-103">Windows Presentation Foundation (WPF) Host (PresentationHost. exe) to aplikacja, która umożliwia obsługiwanie aplikacji WPF w zgodnych przeglądarkach (w tym programu Microsoft Internet Explorer 6 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="d305c-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="d305c-104">Domyślnie Host Windows Presentation Foundation (WPF) jest zarejestrowany jako powłoka i obsługa MIME dla zawartości WPF hostowanej w przeglądarce, która obejmuje:</span><span class="sxs-lookup"><span data-stu-id="d305c-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="d305c-105">Luźno (niekompilowane) pliki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (. XAML).</span><span class="sxs-lookup"><span data-stu-id="d305c-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="d305c-106">Aplikacja przeglądarki XAML (XBAP) (XBAP).</span><span class="sxs-lookup"><span data-stu-id="d305c-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="d305c-107">Dla plików tego typu Windows Presentation Foundation (WPF) Host:</span><span class="sxs-lookup"><span data-stu-id="d305c-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="d305c-108">Uruchamia zarejestrowaną procedurę obsługi HTML do hostowania zawartości Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d305c-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="d305c-109">Ładuje odpowiednie wersje zestawów wymaganych przez środowisko uruchomieniowe języka wspólnego (CLR) i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d305c-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="d305c-110">Zapewnia, że stosowane są odpowiednie poziomy uprawnień dla strefy wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d305c-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="d305c-111">W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="d305c-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="d305c-112">Pomiar</span><span class="sxs-lookup"><span data-stu-id="d305c-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="d305c-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="d305c-113">Parameters</span></span>  
  
|<span data-ttu-id="d305c-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="d305c-114">Parameter</span></span>|<span data-ttu-id="d305c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d305c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d305c-116">nazwa_pliku</span><span class="sxs-lookup"><span data-stu-id="d305c-116">filename</span></span>|<span data-ttu-id="d305c-117">Ścieżka pliku, który ma zostać aktywowany.</span><span class="sxs-lookup"><span data-stu-id="d305c-117">The path of the file to be activated.</span></span> <span data-ttu-id="d305c-118">Może również być identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="d305c-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="d305c-119">-debug</span><span class="sxs-lookup"><span data-stu-id="d305c-119">-debug</span></span>|<span data-ttu-id="d305c-120">Podczas aktywowania aplikacji program nie zatwierdza jej ani nie uruchamia ze sklepu.</span><span class="sxs-lookup"><span data-stu-id="d305c-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="d305c-121">Działa to tylko wtedy, gdy plik lokalny jest aktywowany.</span><span class="sxs-lookup"><span data-stu-id="d305c-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="d305c-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="d305c-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="d305c-123">Używany z wartością adresu URL, aby wskazać PresentationHost. exe, że aplikacja powinna być debugowana tak, jakby została wdrożona z określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="d305c-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="d305c-124">Określa strefę wdrożenia i lokację źródłową.</span><span class="sxs-lookup"><span data-stu-id="d305c-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="d305c-125">— Osadzanie</span><span class="sxs-lookup"><span data-stu-id="d305c-125">-embedding</span></span>|<span data-ttu-id="d305c-126">Wymagane przez OLE.</span><span class="sxs-lookup"><span data-stu-id="d305c-126">Required by OLE.</span></span> <span data-ttu-id="d305c-127">Jeśli parametr `-event` lub `-debug` jest określony, nie trzeba określać `-embedding` parametru, ponieważ ten parametr jest ustawiony wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d305c-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="d305c-128">-Event \<EventName ></span><span class="sxs-lookup"><span data-stu-id="d305c-128">-event \<eventname></span></span>|<span data-ttu-id="d305c-129">Otwórz zdarzenie o tej nazwie i sygnalizuj go, gdy PresentationHost. exe zostanie zainicjowany i będzie gotowy do hostowania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="d305c-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="d305c-130">PresentationHost. exe zakończy się, jeśli wystąpił błąd podczas otwierania zdarzenia, na przykład jeśli nie został jeszcze utworzony.</span><span class="sxs-lookup"><span data-stu-id="d305c-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="d305c-131">-launchApplication \<adres URL ></span><span class="sxs-lookup"><span data-stu-id="d305c-131">-launchApplication \<url></span></span>|<span data-ttu-id="d305c-132">Uruchamia autonomiczną aplikację ClickOnce z podanego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="d305c-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="d305c-133">Stosowane są zasady zabezpieczeń programu Internet Explorer i WinINet dotyczące aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="d305c-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="d305c-134">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="d305c-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="d305c-135">Procedura obsługi powłoki</span><span class="sxs-lookup"><span data-stu-id="d305c-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="d305c-136">Procedura obsługi MIME</span><span class="sxs-lookup"><span data-stu-id="d305c-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="d305c-137">Debugowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d305c-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="d305c-138">Debugowanie programu Visual Studio w strefie</span><span class="sxs-lookup"><span data-stu-id="d305c-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="d305c-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d305c-139">See also</span></span>

- [<span data-ttu-id="d305c-140">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="d305c-140">Security</span></span>](../security-wpf.md)
