---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1a22071696ca012968e042e15cd8a9f4b876fd9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479987"
---
# <a name="filterinputmessage"></a><span data-ttu-id="4577e-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="4577e-102">FilterInputMessage</span></span>
<span data-ttu-id="4577e-103">Metoda wywoływana przez PresentationHost.exe zawsze wtedy, gdy wiadomość zostaje odebrana, chyba że E_NOTIMPL jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="4577e-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4577e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4577e-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4577e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4577e-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="4577e-106">[in] Komunikat WM_INPUT wysyłane do okna, które otrzymuje nieprzetworzone dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4577e-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4577e-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="4577e-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="4577e-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="4577e-108">HRESULT:</span></span>  
  
 <span data-ttu-id="4577e-109">S_OK — filtr nie przetworzył komunikat i dalszego przetwarzania mogą wystąpić.</span><span class="sxs-lookup"><span data-stu-id="4577e-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="4577e-110">S_FALSE — filtr przetworzyć ten komunikat i nie dalszego przetwarzania powinny być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="4577e-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="4577e-111">E_NOTIMPL — Jeśli ta wartość jest zwracana, [filterinputmessage —](../../../../docs/framework/wpf/app-development/filterinputmessage.md) nie zostanie ponownie wywołana.</span><span class="sxs-lookup"><span data-stu-id="4577e-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="4577e-112">To może być zwracane z aplikacji hosta, która jest tylko zainteresowana dostarczanie postępu niestandardowych i interfejsy użytkownika Błąd PresentationHost.exe nie jest zainteresowany przesyłane dalej nieprzetworzone komunikaty wejściowe z PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4577e-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4577e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4577e-113">Remarks</span></span>  
 <span data-ttu-id="4577e-114">PresentationHost.exe jest celem różnych nieprzetworzonych danych wejściowych urządzeń, w tym klawiatury, myszy i zdalnego sterowania.</span><span class="sxs-lookup"><span data-stu-id="4577e-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="4577e-115">Czasami zachowania w aplikacji hosta jest zależny od danych wejściowych, które w przeciwnym razie może być zużyte przez PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4577e-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="4577e-116">Na przykład aplikacja hosta może zależeć odbierania niektórych komunikatów wejściowych, aby określić, czy należy wyświetlać elementy interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4577e-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="4577e-117">Aby umożliwić aplikacji hosta otrzymywać niezbędne komunikaty wejściowe, aby zapewnić następujące zachowania, PresentationHost.exe przekazuje odpowiednie nieprzetworzone komunikaty wejściowe do aplikacji hostowanej przez wywołanie metody [filterinputmessage —](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="4577e-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="4577e-118">Hostowana aplikacja odbiera nieprzetworzone komunikaty wejściowe przez zarejestrowanie kodowań z zestawem nieprzetworzonych danych wejściowych (urządzenia ludzi interfejsu) zwracane przez [getrawinputdevices —](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="4577e-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4577e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4577e-119">See Also</span></span>  
 [<span data-ttu-id="4577e-120">WM_INPUT powiadomień</span><span class="sxs-lookup"><span data-stu-id="4577e-120">WM_INPUT Notification</span></span>](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
