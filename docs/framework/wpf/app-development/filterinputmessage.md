---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 69bc1e973b690454bcf91487c12dc4ce0ac46a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="filterinputmessage"></a><span data-ttu-id="85fb3-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="85fb3-102">FilterInputMessage</span></span>
<span data-ttu-id="85fb3-103">Metoda wywoływana przez PresentationHost.exe zawsze, gdy wiadomość zostanie odebrana, chyba że E_NOTIMPL jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="85fb3-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85fb3-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85fb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85fb3-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="85fb3-106">[in] WM_INPUT komunikat wysyłany do okna, które otrzymuje nieprzetworzone dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="85fb3-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="85fb3-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="85fb3-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="85fb3-108">WYNIK HRESULT:</span><span class="sxs-lookup"><span data-stu-id="85fb3-108">HRESULT:</span></span>  
  
 <span data-ttu-id="85fb3-109">S_OK — filtr nie przetworzyć komunikatu i dalsze przetwarzanie nie może występować.</span><span class="sxs-lookup"><span data-stu-id="85fb3-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="85fb3-110">Wartości S_FALSE - przetworzyć filtru ten komunikat i nie dalsze przetwarzanie powinna się odbyć.</span><span class="sxs-lookup"><span data-stu-id="85fb3-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="85fb3-111">E_NOTIMPL — Jeśli ta wartość jest zwracana, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) nie zostanie ponownie wywołany.</span><span class="sxs-lookup"><span data-stu-id="85fb3-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="85fb3-112">Może to być zwracane z aplikacji hosta, który tylko zainteresowani dostarczanie niestandardowych postęp i interfejsów użytkownika Błąd PresentationHost.exe nie jest zainteresowana przesyłane dalej komunikaty wejściowe pierwotnych z PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="85fb3-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85fb3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85fb3-113">Remarks</span></span>  
 <span data-ttu-id="85fb3-114">PresentationHost.exe jest elementem docelowym różnych raw wejściowych urządzeń, takich jak klawiatura, mysz i zdalnego sterowania.</span><span class="sxs-lookup"><span data-stu-id="85fb3-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="85fb3-115">Czasami zachowania w aplikacji hosta jest zależny od danych wejściowych, które w przeciwnym razie może być zużyte przez PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="85fb3-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="85fb3-116">Na przykład aplikacja hosta może zależeć od odbieranie komunikatów wejściowych do ustalenia, czy wyświetlać elementy interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="85fb3-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="85fb3-117">Aby umożliwić aplikacji hosta do odbierania niezbędne komunikaty wejściowe zapewnienie te zachowania, PresentationHost.exe przekazuje odpowiednie komunikaty wejściowe nieprzetworzone dla aplikacji hostowanej przez wywołanie metody [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="85fb3-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="85fb3-118">Hostowana aplikacja odbiera raw komunikaty wejściowe rejestrując z zestawem raw wejściowych (urządzenia człowieka interfejsu) zwrócone przez [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="85fb3-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fb3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85fb3-119">See Also</span></span>  
 [<span data-ttu-id="85fb3-120">WM_INPUT powiadomień</span><span class="sxs-lookup"><span data-stu-id="85fb3-120">WM_INPUT Notification</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
