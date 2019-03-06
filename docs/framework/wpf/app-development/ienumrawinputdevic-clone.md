---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: a4c5e7db813089d1dd138416ac54dd4be467b87b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355024"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="ea0d1-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="ea0d1-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="ea0d1-103">Tworzy inny moduł wyliczający pierwotne urządzenia wejściowego o ten sam stan jako bieżący modułu wyliczającego do wykonywania iteracji w tej samej listy.</span><span class="sxs-lookup"><span data-stu-id="ea0d1-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea0d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea0d1-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea0d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea0d1-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="ea0d1-106">[out] Adres zmiennej danych wyjściowych, który odbiera [ienumrawinputdevice —](ienumrawinputdevice.md) wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ea0d1-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="ea0d1-107">Jeśli metoda zakończy się niepowodzeniem, wartość tej zmiennej danych wyjściowych jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="ea0d1-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ea0d1-108">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="ea0d1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="ea0d1-109">HRESULT: Ta metoda obsługuje standardowe wartości zwracane E_INVALIDARG E_OUTOFMEMORY i wartość E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="ea0d1-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea0d1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea0d1-110">Remarks</span></span>  
 <span data-ttu-id="ea0d1-111">Ta metoda umożliwia rejestrowanie punkt w kolejności wyliczenia, aby można było powrócić do tego punktu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="ea0d1-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="ea0d1-112">Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający, niezależnie od pierwszego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="ea0d1-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
