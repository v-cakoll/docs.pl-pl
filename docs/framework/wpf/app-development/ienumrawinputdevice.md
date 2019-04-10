---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225524"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="aab0f-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="aab0f-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="aab0f-103">Ten interfejs wylicza pierwotne urządzenia wejściowe i jest używana tylko przez PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="aab0f-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aab0f-104">Ten interfejs API jest tylko przeznaczone i obsługiwane do użytku na komputerze klienckim lokalne</span><span class="sxs-lookup"><span data-stu-id="aab0f-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="aab0f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="aab0f-105">Members</span></span>  
  
|<span data-ttu-id="aab0f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="aab0f-106">Member</span></span>|<span data-ttu-id="aab0f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aab0f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aab0f-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="aab0f-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="aab0f-109">Wylicza następnego `celt` elementów (czyli RAWINPUTDEVICE struktury) na liście modułu wyliczającego, zwracając je w `rgelt` wraz z liczbą rzeczywiste elementy wyliczenia `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="aab0f-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="aab0f-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="aab0f-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="aab0f-111">Powoduje, że moduł wyliczający, aby pominąć następnego `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nie będzie zwracać tych elementów.</span><span class="sxs-lookup"><span data-stu-id="aab0f-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="aab0f-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="aab0f-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="aab0f-113">Resetuje sekwencji wyliczenia na początku.</span><span class="sxs-lookup"><span data-stu-id="aab0f-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="aab0f-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="aab0f-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="aab0f-115">Tworzy inny moduł wyliczający pierwotne urządzenia wejściowego o ten sam stan jako bieżący modułu wyliczającego do wykonywania iteracji w tej samej listy.</span><span class="sxs-lookup"><span data-stu-id="aab0f-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aab0f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aab0f-116">See also</span></span>

- [<span data-ttu-id="aab0f-117">Temat nieprzetworzone dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="aab0f-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
