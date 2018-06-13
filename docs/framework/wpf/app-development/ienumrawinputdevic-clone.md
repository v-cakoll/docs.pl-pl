---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: da089e5342e641ffebe22ca6a4a593f97faeb89c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545349"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="84fa1-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="84fa1-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="84fa1-103">Tworzy inny moduł wyliczający raw urządzenia wejściowego z takim samym stanie, aby jako bieżącego modułu wyliczającego, aby przejść przez tę samą listę.</span><span class="sxs-lookup"><span data-stu-id="84fa1-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84fa1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84fa1-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84fa1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84fa1-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="84fa1-106">[out] Adresu zmiennej danych wyjściowych, który odbiera [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="84fa1-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="84fa1-107">Jeśli metoda zakończy się niepowodzeniem, wartość tej zmiennej danych wyjściowych jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="84fa1-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="84fa1-108">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="84fa1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="84fa1-109">Wynik HRESULT: Ta metoda obsługuje standardowe wartości zwracanych E_INVALIDARG E_OUTOFMEMORY i E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="84fa1-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84fa1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84fa1-110">Remarks</span></span>  
 <span data-ttu-id="84fa1-111">Ta metoda umożliwia rejestrowanie punktu w sekwencji wyliczenie aby powrócić do tego punktu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="84fa1-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="84fa1-112">Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający niezależnie od pierwszego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="84fa1-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
