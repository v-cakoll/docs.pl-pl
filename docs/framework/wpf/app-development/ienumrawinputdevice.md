---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964764"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="adea0-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="adea0-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="adea0-103">Ten interfejs wylicza pierwotne urządzenia wejściowe i jest używany tylko przez PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="adea0-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adea0-104">Ten interfejs API jest przeznaczony tylko do użytku i jest obsługiwany na lokalnym komputerze klienckim</span><span class="sxs-lookup"><span data-stu-id="adea0-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="adea0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="adea0-105">Members</span></span>  
  
|<span data-ttu-id="adea0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="adea0-106">Member</span></span>|<span data-ttu-id="adea0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="adea0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adea0-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="adea0-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="adea0-109">Wylicza następne `celt` elementy (czyli struktury RAWINPUTDEVICE) na liście modułu wyliczającego, zwracając `rgelt` je wraz z rzeczywistą liczbą wyliczeniowych elementów w `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="adea0-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="adea0-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="adea0-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="adea0-111">Instruuje moduł wyliczający, aby pominąć `celt` kolejne elementy w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) nie zwróci tych elementów.</span><span class="sxs-lookup"><span data-stu-id="adea0-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="adea0-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="adea0-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="adea0-113">Resetuje sekwencję wyliczenia na początek.</span><span class="sxs-lookup"><span data-stu-id="adea0-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="adea0-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="adea0-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="adea0-115">Tworzy inny nieprzetworzony moduł wyliczający urządzenia wejściowe z tym samym stanem co bieżący moduł wyliczający, aby wykonać iterację na tej samej liście.</span><span class="sxs-lookup"><span data-stu-id="adea0-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adea0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adea0-116">See also</span></span>

- [<span data-ttu-id="adea0-117">Informacje o nieprzetworzonym wejściu</span><span class="sxs-lookup"><span data-stu-id="adea0-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
