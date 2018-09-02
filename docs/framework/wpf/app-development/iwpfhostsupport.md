---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 57d9ef87a078655a89a5869a48a1bd16f21b000f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385157"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="41355-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="41355-102">IWpfHostSupport</span></span>
<span data-ttu-id="41355-103">Aplikacje obsługujące [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartości za pośrednictwem PresentationHost.exe implementować ten interfejs zapewnia punkt integracji między hostem a PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="41355-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41355-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41355-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="41355-105"> aplikacje, takie jak przeglądarki sieci Web może obsługiwać [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźno XAML.</span><span class="sxs-lookup"><span data-stu-id="41355-105"> applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="41355-106">Na hoście [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacji Utwórz wystąpienie obiektu [formantu WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="41355-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="41355-107">Będzie hostowana [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] tworzy wystąpienie PresentationHost.exe, co zapewnia hostowanej [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości do hosta w celu wyświetlania w [formantu WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="41355-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="41355-108">Integracja włączane przez `IWpfHostSupport` umożliwia PresentationHost.exe do:</span><span class="sxs-lookup"><span data-stu-id="41355-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
-   <span data-ttu-id="41355-109">Odnajdywanie i rejestrowanie w usłudze nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="41355-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
-   <span data-ttu-id="41355-110">Komunikaty wejściowe z pierwotnych danych wejściowych zarejestrowanych i przekazywania wiadomości w odpowiedniej aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="41355-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
-   <span data-ttu-id="41355-111">Wyślij zapytanie do aplikacji hosta dla niestandardowych interfejsów użytkownika postępu i błędów.</span><span class="sxs-lookup"><span data-stu-id="41355-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41355-112">Ten interfejs API jest tylko przeznaczone i obsługiwane do użytku na komputerze klienckim lokalne</span><span class="sxs-lookup"><span data-stu-id="41355-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="41355-113">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="41355-113">Members</span></span>  
  
|<span data-ttu-id="41355-114">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="41355-114">Member</span></span>|<span data-ttu-id="41355-115">Opis</span><span class="sxs-lookup"><span data-stu-id="41355-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41355-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="41355-116">GetRawInputDevices</span></span>](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|<span data-ttu-id="41355-117">Umożliwia PresentationHost.exe odnajdywania nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="41355-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="41355-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="41355-118">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|<span data-ttu-id="41355-119">Metoda wywoływana przez PresentationHost.exe zawsze wtedy, gdy wiadomość zostaje odebrana, chyba że E_NOTIMPL jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="41355-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="41355-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="41355-120">GetCustomUI</span></span>](../../../../docs/framework/wpf/app-development/getcustomui.md)|<span data-ttu-id="41355-121">Domyślnie PresentationHost.exe zawiera swój własny postęp wdrażania i Błąd wdrażania interfejsów użytkownika, które są wyświetlane podczas wdrażania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="41355-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
