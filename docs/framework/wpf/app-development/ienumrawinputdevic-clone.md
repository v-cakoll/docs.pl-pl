---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485411"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="6a07c-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="6a07c-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="6a07c-103">Tworzy inny moduł wyliczający pierwotne urządzenia wejściowego o ten sam stan jako bieżący modułu wyliczającego do wykonywania iteracji w tej samej listy.</span><span class="sxs-lookup"><span data-stu-id="6a07c-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a07c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a07c-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a07c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a07c-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="6a07c-106">[out] Adres zmiennej danych wyjściowych, który odbiera [ienumrawinputdevice —](ienumrawinputdevice.md) wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6a07c-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="6a07c-107">Jeśli metoda zakończy się niepowodzeniem, wartość tej zmiennej danych wyjściowych jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="6a07c-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="6a07c-108">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="6a07c-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="6a07c-109">HRESULT: Ta metoda obsługuje standardowe wartości zwracane E_INVALIDARG E_OUTOFMEMORY i wartość E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="6a07c-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a07c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a07c-110">Remarks</span></span>  
 <span data-ttu-id="6a07c-111">Ta metoda umożliwia rejestrowanie punkt w kolejności wyliczenia, aby można było powrócić do tego punktu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="6a07c-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="6a07c-112">Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający, niezależnie od pierwszego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="6a07c-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
