---
title: IEnumRAWINPUTDEVICE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f9ebd0aee5041ef8a8a7cc44261fa69e3da1fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="880fb-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="880fb-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="880fb-103">Ten interfejs wylicza raw urządzenia wejściowe i jest używana tylko przez PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="880fb-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="880fb-104">Ten interfejs API jest tylko przeznaczone i obsługiwana na maszynie lokalnej klienta</span><span class="sxs-lookup"><span data-stu-id="880fb-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="880fb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="880fb-105">Members</span></span>  
  
|<span data-ttu-id="880fb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="880fb-106">Member</span></span>|<span data-ttu-id="880fb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="880fb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="880fb-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="880fb-108">IEnumRAWINPUTDEVIC:Next</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|<span data-ttu-id="880fb-109">Wylicza następnej `celt` elementy (to znaczy RAWINPUTDEVICE struktury) na liście modułu wyliczającego, zwracając je w `rgelt` wraz z rzeczywistą liczbę elementów wyliczane w `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="880fb-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="880fb-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="880fb-110">IEnumRAWINPUTDEVIC:Skip</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|<span data-ttu-id="880fb-111">Powoduje, że moduł wyliczający, aby przejść dalej `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) nie zwróci tych elementów.</span><span class="sxs-lookup"><span data-stu-id="880fb-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="880fb-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="880fb-112">IEnumRAWINPUTDEVIC:Reset</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|<span data-ttu-id="880fb-113">Resetuje sekwencji wyliczenia na początku.</span><span class="sxs-lookup"><span data-stu-id="880fb-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="880fb-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="880fb-114">IEnumRAWINPUTDEVIC:Clone</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|<span data-ttu-id="880fb-115">Tworzy inny moduł wyliczający raw urządzenia wejściowego z takim samym stanie, aby jako bieżącego modułu wyliczającego, aby przejść przez tę samą listę.</span><span class="sxs-lookup"><span data-stu-id="880fb-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="880fb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="880fb-116">See Also</span></span>  
 [<span data-ttu-id="880fb-117">O nieprzetworzone dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="880fb-117">About Raw Input</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
