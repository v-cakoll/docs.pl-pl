---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: e7bc6f2c96413f3898a17b541733eeecd6a260f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375067"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="5c72b-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="5c72b-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="5c72b-103">Ten interfejs wylicza pierwotne urządzenia wejściowe i jest używana tylko przez PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="5c72b-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c72b-104">Ten interfejs API jest tylko przeznaczone i obsługiwane do użytku na komputerze klienckim lokalne</span><span class="sxs-lookup"><span data-stu-id="5c72b-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="5c72b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5c72b-105">Members</span></span>  
  
|<span data-ttu-id="5c72b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5c72b-106">Member</span></span>|<span data-ttu-id="5c72b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5c72b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c72b-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="5c72b-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="5c72b-109">Wylicza następnego `celt` elementów (czyli RAWINPUTDEVICE struktury) na liście modułu wyliczającego, zwracając je w `rgelt` wraz z liczbą rzeczywiste elementy wyliczenia `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="5c72b-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="5c72b-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="5c72b-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="5c72b-111">Powoduje, że moduł wyliczający, aby pominąć następnego `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nie będzie zwracać tych elementów.</span><span class="sxs-lookup"><span data-stu-id="5c72b-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="5c72b-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="5c72b-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="5c72b-113">Resetuje sekwencji wyliczenia na początku.</span><span class="sxs-lookup"><span data-stu-id="5c72b-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="5c72b-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="5c72b-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="5c72b-115">Tworzy inny moduł wyliczający pierwotne urządzenia wejściowego o ten sam stan jako bieżący modułu wyliczającego do wykonywania iteracji w tej samej listy.</span><span class="sxs-lookup"><span data-stu-id="5c72b-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c72b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c72b-116">See also</span></span>
- [<span data-ttu-id="5c72b-117">Temat nieprzetworzone dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="5c72b-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
