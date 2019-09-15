---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1453946766e33843ae9e56f7a7f4dbf1678b81b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991385"
---
# <a name="filterinputmessage"></a><span data-ttu-id="564a2-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="564a2-102">FilterInputMessage</span></span>
<span data-ttu-id="564a2-103">Wywoływana przez PresentationHost. exe za każdym razem, gdy wiadomość zostanie odebrana, chyba że zostanie zwrócona wartość E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="564a2-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="564a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="564a2-104">Syntax</span></span>  
  
```cpp  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a><span data-ttu-id="564a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="564a2-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="564a2-106">podczas Wiadomość WM_INPUT wysłana do okna, które pobiera nieprzetworzone dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="564a2-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="564a2-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="564a2-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="564a2-108">WYNIK</span><span class="sxs-lookup"><span data-stu-id="564a2-108">HRESULT:</span></span>  
  
 <span data-ttu-id="564a2-109">S_OK — filtr nie przetworzył komunikatu i może wystąpić dalsze przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="564a2-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="564a2-110">S_FALSE — filtr przetworzył ten komunikat i nie powinno wystąpić dalsze przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="564a2-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="564a2-111">E_NOTIMPL — w przypadku zwrócenia wartości [FilterInputMessage](filterinputmessage.md) nie jest ponownie wywoływana.</span><span class="sxs-lookup"><span data-stu-id="564a2-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="564a2-112">Może to zostać zwrócone z aplikacji hosta, która jest interesująca tylko w celu udostępnienia niestandardowego postępu i błędów interfejsów użytkownika do PresentationHost. exe nie interesuje przekazanie pierwotnych komunikatów wejściowych z PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="564a2-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="564a2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="564a2-113">Remarks</span></span>  
 <span data-ttu-id="564a2-114">PresentationHost. exe jest elementem docelowym różnych nieprzetworzonych urządzeń wejściowych, w tym klawiatury, myszy i pilotów.</span><span class="sxs-lookup"><span data-stu-id="564a2-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="564a2-115">Czasami zachowanie w aplikacji hosta jest zależne od danych wejściowych, które w przeciwnym razie byłyby używane przez PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="564a2-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="564a2-116">Na przykład aplikacja hosta może zależeć od otrzymywania pewnych komunikatów wejściowych, aby określić, czy mają być wyświetlane konkretne elementy interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="564a2-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="564a2-117">Aby umożliwić aplikacji hosta otrzymywanie niezbędnych komunikatów wejściowych w celu zapewnienia tych zachowań, PresentationHost. exe przekazuje odpowiednie nieprzetworzone komunikaty wejściowe do hostowanej aplikacji przez wywołanie [FilterInputMessage](filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="564a2-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="564a2-118">Hostowana aplikacja odbiera nieprzetworzone komunikaty wejściowe przez zarejestrowanie się w zestawie nieprzetworzonych urządzeń wejściowych (urządzenia interfejsu ludzkiego) zwracanych przez [GetRawInputDevices](getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="564a2-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="564a2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="564a2-119">See also</span></span>

- [<span data-ttu-id="564a2-120">WM_INPUT komunikat</span><span class="sxs-lookup"><span data-stu-id="564a2-120">WM_INPUT message</span></span>](/windows/desktop/inputdev/wm-input)
