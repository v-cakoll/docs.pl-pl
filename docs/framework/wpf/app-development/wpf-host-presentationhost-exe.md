---
title: Host WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 16618042324387bfc15f4685f4759378c50a80b7
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401718"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="892d7-102">Host WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="892d7-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="892d7-103">Windows Presentation Foundation (WPF) Host (PresentationHost. exe) to aplikacja, która umożliwia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługiwanie aplikacji w zgodnych przeglądarkach ( [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] w tym i nowszych).</span><span class="sxs-lookup"><span data-stu-id="892d7-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="892d7-104">Domyślnie Host Windows Presentation Foundation (WPF) jest zarejestrowany jako powłoka i [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] program obsługi dla zawartości obsługiwanej [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przez przeglądarkę, w tym:</span><span class="sxs-lookup"><span data-stu-id="892d7-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="892d7-105">Luźne (Nieskompilowane) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki (. XAML).</span><span class="sxs-lookup"><span data-stu-id="892d7-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]<span data-ttu-id="892d7-106">(. XBAP).</span><span class="sxs-lookup"><span data-stu-id="892d7-106">(.xbap).</span></span>  
  
 <span data-ttu-id="892d7-107">Dla plików tego typu Windows Presentation Foundation (WPF) Host:</span><span class="sxs-lookup"><span data-stu-id="892d7-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="892d7-108">Uruchamia zarejestrowaną [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] procedurę obsługi do obsługi zawartości Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="892d7-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="892d7-109">Ładuje odpowiednie wersje zestawów wymaganych przez środowisko uruchomieniowe języka wspólnego (CLR) i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="892d7-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="892d7-110">Zapewnia, że stosowane są odpowiednie poziomy uprawnień dla strefy wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="892d7-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="892d7-111">W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="892d7-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="892d7-112">Użycie</span><span class="sxs-lookup"><span data-stu-id="892d7-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="892d7-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="892d7-113">Parameters</span></span>  
  
|<span data-ttu-id="892d7-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="892d7-114">Parameter</span></span>|<span data-ttu-id="892d7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="892d7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="892d7-116">nazwa_pliku</span><span class="sxs-lookup"><span data-stu-id="892d7-116">filename</span></span>|<span data-ttu-id="892d7-117">Ścieżka pliku, który ma zostać aktywowany.</span><span class="sxs-lookup"><span data-stu-id="892d7-117">The path of the file to be activated.</span></span> <span data-ttu-id="892d7-118">Może być [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]również.</span><span class="sxs-lookup"><span data-stu-id="892d7-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="892d7-119">-debug</span><span class="sxs-lookup"><span data-stu-id="892d7-119">-debug</span></span>|<span data-ttu-id="892d7-120">Podczas aktywowania aplikacji program nie zatwierdza jej ani nie uruchamia ze sklepu.</span><span class="sxs-lookup"><span data-stu-id="892d7-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="892d7-121">Działa to tylko wtedy, gdy plik lokalny jest aktywowany.</span><span class="sxs-lookup"><span data-stu-id="892d7-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="892d7-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="892d7-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="892d7-123">Używane z [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] wartością wskazującą PresentationHost. exe, że aplikacja powinna być debugowana tak, jakby została wdrożona z określonego [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]elementu.</span><span class="sxs-lookup"><span data-stu-id="892d7-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="892d7-124">Określa strefę wdrożenia i lokację źródłową.</span><span class="sxs-lookup"><span data-stu-id="892d7-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="892d7-125">— Osadzanie</span><span class="sxs-lookup"><span data-stu-id="892d7-125">-embedding</span></span>|<span data-ttu-id="892d7-126">Wymagane przez OLE.</span><span class="sxs-lookup"><span data-stu-id="892d7-126">Required by OLE.</span></span> <span data-ttu-id="892d7-127">Jeśli parametr `-debug` `-embedding` lub jest określony, nie trzeba określać parametru, ponieważ ten parametr jest ustawiony wewnętrznie. `-event`</span><span class="sxs-lookup"><span data-stu-id="892d7-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="892d7-128">-Event \<EventName ></span><span class="sxs-lookup"><span data-stu-id="892d7-128">-event \<eventname></span></span>|<span data-ttu-id="892d7-129">Otwórz zdarzenie o tej nazwie i sygnalizuj go, gdy PresentationHost. exe zostanie zainicjowany i będzie gotowy do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="892d7-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="892d7-130">PresentationHost. exe zakończy się, jeśli wystąpił błąd podczas otwierania zdarzenia, na przykład jeśli nie został jeszcze utworzony.</span><span class="sxs-lookup"><span data-stu-id="892d7-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="892d7-131">-launchApplication \<adres URL ></span><span class="sxs-lookup"><span data-stu-id="892d7-131">-launchApplication \<url></span></span>|<span data-ttu-id="892d7-132">Uruchamia autonomiczną aplikację ClickOnce z podanego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="892d7-132">Launches a standalone ClickOnce application from the specified URL.</span></span> [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]<span data-ttu-id="892d7-133">są stosowane zasady zabezpieczeń WinINet dotyczące aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="892d7-133">and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="892d7-134">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="892d7-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="892d7-135">Procedura obsługi powłoki</span><span class="sxs-lookup"><span data-stu-id="892d7-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="892d7-136">Procedura obsługi MIME</span><span class="sxs-lookup"><span data-stu-id="892d7-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="892d7-137">Debugowanie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="892d7-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="892d7-138">Debugowanie programu Visual Studio w strefie</span><span class="sxs-lookup"><span data-stu-id="892d7-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="892d7-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="892d7-139">See also</span></span>

- [<span data-ttu-id="892d7-140">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="892d7-140">Security</span></span>](../security-wpf.md)
