---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 074167111b78edc517dda019465260d0acd54737
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006697"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="b5371-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="b5371-102">IWpfHostSupport</span></span>
<span data-ttu-id="b5371-103">Aplikacje obsługujące [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartości za pośrednictwem PresentationHost.exe implementować ten interfejs zapewnia punkt integracji między hostem a PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="b5371-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5371-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5371-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] <span data-ttu-id="b5371-105">aplikacje, takie jak przeglądarki sieci Web może obsługiwać [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźno XAML.</span><span class="sxs-lookup"><span data-stu-id="b5371-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="b5371-106">Na hoście [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacji Utwórz wystąpienie obiektu [formantu WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="b5371-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="b5371-107">Będzie hostowana [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] tworzy wystąpienie PresentationHost.exe, co zapewnia hostowanej [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości do hosta w celu wyświetlania w [formantu WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="b5371-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="b5371-108">Integracja włączane przez `IWpfHostSupport` umożliwia PresentationHost.exe do:</span><span class="sxs-lookup"><span data-stu-id="b5371-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="b5371-109">Odnajdywanie i rejestrowanie w usłudze nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="b5371-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="b5371-110">Komunikaty wejściowe z pierwotnych danych wejściowych zarejestrowanych i przekazywania wiadomości w odpowiedniej aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="b5371-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="b5371-111">Wyślij zapytanie do aplikacji hosta dla niestandardowych interfejsów użytkownika postępu i błędów.</span><span class="sxs-lookup"><span data-stu-id="b5371-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5371-112">Ten interfejs API jest tylko przeznaczone i obsługiwane do użytku na komputerze klienckim lokalne</span><span class="sxs-lookup"><span data-stu-id="b5371-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="b5371-113">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b5371-113">Members</span></span>  
  
|<span data-ttu-id="b5371-114">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b5371-114">Member</span></span>|<span data-ttu-id="b5371-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b5371-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5371-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="b5371-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="b5371-117">Umożliwia PresentationHost.exe odnajdywania nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="b5371-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="b5371-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="b5371-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="b5371-119">Metoda wywoływana przez PresentationHost.exe zawsze wtedy, gdy wiadomość zostaje odebrana, chyba że E_NOTIMPL jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="b5371-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="b5371-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="b5371-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="b5371-121">Domyślnie PresentationHost.exe zawiera swój własny postęp wdrażania i Błąd wdrażania interfejsów użytkownika, które są wyświetlane podczas wdrażania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="b5371-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
