---
title: IWpfHostSupport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85d4ed09d6c5ca17e148d531e6aac483ff737d51
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="5a75d-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="5a75d-102">IWpfHostSupport</span></span>
<span data-ttu-id="5a75d-103">Aplikacje, które obsługują [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartości za pośrednictwem PresentationHost.exe implementuje ten interfejs zapewnia punkt integracji między hostem a PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="5a75d-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a75d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a75d-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="5a75d-105">aplikacje, takie jak przeglądarki sieci Web mogą obsługiwać [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartość, łącznie z [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] utrata XAML.</span><span class="sxs-lookup"><span data-stu-id="5a75d-105"> applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="5a75d-106">Na hoście [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacji Utwórz wystąpienie [formant WebBrowser](http://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="5a75d-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](http://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="5a75d-107">Ma być obsługiwana [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] tworzy wystąpienie PresentationHost.exe, która zapewnia hostowanej [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości do hosta do wyświetlenia w [formant WebBrowser](http://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="5a75d-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](http://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="5a75d-108">Integracja włączane przez `IWpfHostSupport` umożliwia PresentationHost.exe do:</span><span class="sxs-lookup"><span data-stu-id="5a75d-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
-   <span data-ttu-id="5a75d-109">Odnajdź i zarejestruj z urządzeniami wejściowych surowego (człowieka interfejsu urządzenia), które jest zainteresowana aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="5a75d-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
-   <span data-ttu-id="5a75d-110">Komunikaty wejściowe z zarejestrowanego urządzenia wejściowe pierwotnych i przekazywania wiadomości odpowiednie do aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="5a75d-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
-   <span data-ttu-id="5a75d-111">Wyślij zapytanie do aplikacji hosta dla niestandardowych interfejsów użytkownika postępu i błędów.</span><span class="sxs-lookup"><span data-stu-id="5a75d-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a75d-112">Ten interfejs API jest tylko przeznaczone i obsługiwana na maszynie lokalnej klienta</span><span class="sxs-lookup"><span data-stu-id="5a75d-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="5a75d-113">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5a75d-113">Members</span></span>  
  
|<span data-ttu-id="5a75d-114">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5a75d-114">Member</span></span>|<span data-ttu-id="5a75d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5a75d-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a75d-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="5a75d-116">GetRawInputDevices</span></span>](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|<span data-ttu-id="5a75d-117">Umożliwia PresentationHost.exe w celu odnalezienia urządzeń wejściowych raw (człowieka interfejsu urządzenia), które jest zainteresowana aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="5a75d-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="5a75d-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="5a75d-118">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|<span data-ttu-id="5a75d-119">Metoda wywoływana przez PresentationHost.exe zawsze, gdy wiadomość zostanie odebrana, chyba że E_NOTIMPL jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="5a75d-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="5a75d-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="5a75d-120">GetCustomUI</span></span>](../../../../docs/framework/wpf/app-development/getcustomui.md)|<span data-ttu-id="5a75d-121">Domyślnie PresentationHost.exe zapewnia własne postępu wdrożenia i Błąd wdrażania interfejsów użytkownika, które są wyświetlane po wdrożeniu zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="5a75d-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
