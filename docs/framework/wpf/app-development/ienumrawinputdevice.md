---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: e07b646c51a143cc15fd125dc295ed90f605328f
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745654"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="1e82d-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="1e82d-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="1e82d-103">Ten interfejs wylicza pierwotne urządzenia wejściowe i jest używana tylko przez PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="1e82d-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e82d-104">Ten interfejs API jest tylko przeznaczone i obsługiwane do użytku na komputerze klienckim lokalne</span><span class="sxs-lookup"><span data-stu-id="1e82d-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="1e82d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1e82d-105">Members</span></span>  
  
|<span data-ttu-id="1e82d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1e82d-106">Member</span></span>|<span data-ttu-id="1e82d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1e82d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e82d-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="1e82d-108">IEnumRAWINPUTDEVIC:Next</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|<span data-ttu-id="1e82d-109">Wylicza następnego `celt` elementów (czyli RAWINPUTDEVICE struktury) na liście modułu wyliczającego, zwracając je w `rgelt` wraz z liczbą rzeczywiste elementy wyliczenia `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="1e82d-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="1e82d-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="1e82d-110">IEnumRAWINPUTDEVIC:Skip</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|<span data-ttu-id="1e82d-111">Powoduje, że moduł wyliczający, aby pominąć następnego `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) nie będzie zwracać tych elementów.</span><span class="sxs-lookup"><span data-stu-id="1e82d-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="1e82d-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="1e82d-112">IEnumRAWINPUTDEVIC:Reset</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|<span data-ttu-id="1e82d-113">Resetuje sekwencji wyliczenia na początku.</span><span class="sxs-lookup"><span data-stu-id="1e82d-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="1e82d-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="1e82d-114">IEnumRAWINPUTDEVIC:Clone</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|<span data-ttu-id="1e82d-115">Tworzy inny moduł wyliczający pierwotne urządzenia wejściowego o ten sam stan jako bieżący modułu wyliczającego do wykonywania iteracji w tej samej listy.</span><span class="sxs-lookup"><span data-stu-id="1e82d-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e82d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e82d-116">See also</span></span>
- [<span data-ttu-id="1e82d-117">Temat nieprzetworzone dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="1e82d-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
