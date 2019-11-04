---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 91a29233d12a842a64b7d3dd497312f6dc6742ca
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423651"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="3f2c3-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="3f2c3-102">IWpfHostSupport</span></span>
<span data-ttu-id="3f2c3-103">Aplikacje, które hostuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartość za pomocą PresentationHost. exe implementują ten interfejs, aby zapewnić punkt integracji między hostem a PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f2c3-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f2c3-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] <span data-ttu-id="3f2c3-105">aplikacje, takie jak przeglądarki sieci Web, mogą hostować zawartość WPF, w tym aplikacje przeglądarki XAML (XBAP) i luźny kod XAML.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-105">applications such as Web browsers can host WPF content, including XAML browser applications (XBAPs) and loose XAML.</span></span> <span data-ttu-id="3f2c3-106">Aby hostować zawartość WPF, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje tworzą wystąpienie [kontrolki WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="3f2c3-106">To host WPF content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="3f2c3-107">Aby można było hostować, WPF tworzy wystąpienie programu PresentationHost. exe, które udostępnia hostowaną zawartość WPF do hosta na potrzeby wyświetlania w [kontrolce WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="3f2c3-107">To be hosted, WPF creates an instance of PresentationHost.exe, which provides the hosted WPF content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="3f2c3-108">Integracja włączona przez `IWpfHostSupport` umożliwia programowi PresentationHost. exe:</span><span class="sxs-lookup"><span data-stu-id="3f2c3-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="3f2c3-109">Wykrywaj i Rejestruj na nieprzetworzonych urządzeniach wejściowych (urządzenia interfejsu ludzkiego), których aplikacja hosta jest zainteresowana.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="3f2c3-110">Odbieraj komunikaty wejściowe z zarejestrowanych nieprzetworzonych urządzeń wejściowych i przekazuj odpowiednie komunikaty do aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="3f2c3-111">Zbadaj aplikację hosta pod kątem niestandardowego postępu i błędów interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f2c3-112">Ten interfejs API jest przeznaczony tylko do użytku i jest obsługiwany na lokalnym komputerze klienckim</span><span class="sxs-lookup"><span data-stu-id="3f2c3-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="3f2c3-113">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3f2c3-113">Members</span></span>  
  
|<span data-ttu-id="3f2c3-114">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3f2c3-114">Member</span></span>|<span data-ttu-id="3f2c3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3f2c3-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f2c3-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="3f2c3-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="3f2c3-117">Zezwala programowi PresentationHost. exe na odnajdywanie nieprzetworzonych urządzeń wejściowych (urządzeń z interfejsem ludzkim), których aplikacja hosta interesuje.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="3f2c3-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="3f2c3-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="3f2c3-119">Wywoływana przez PresentationHost. exe za każdym razem, gdy wiadomość zostanie odebrana, chyba że zostanie zwrócona wartość E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="3f2c3-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="3f2c3-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="3f2c3-121">Domyślnie program PresentationHost. exe udostępnia swój własny postęp wdrażania i interfejsy użytkownika błędów wdrażania, które są wyświetlane podczas wdrażania zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="3f2c3-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
