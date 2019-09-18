---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053419"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="a14e7-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="a14e7-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="a14e7-103">Tworzy inny nieprzetworzony moduł wyliczający urządzenia wejściowe z tym samym stanem co bieżący moduł wyliczający, aby wykonać iterację na tej samej liście.</span><span class="sxs-lookup"><span data-stu-id="a14e7-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a14e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a14e7-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a14e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a14e7-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="a14e7-106">określoną Adres zmiennej wyjściowej, która odbiera wskaźnik interfejsu [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) .</span><span class="sxs-lookup"><span data-stu-id="a14e7-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="a14e7-107">Jeśli metoda nie powiedzie się, wartość tej zmiennej wyjściowej jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="a14e7-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a14e7-108">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="a14e7-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="a14e7-109">WYNIK Ta metoda obsługuje standardowe wartości zwracane E_INVALIDARG, E_OUTOFMEMORY i E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="a14e7-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a14e7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a14e7-110">Remarks</span></span>  
 <span data-ttu-id="a14e7-111">Ta metoda umożliwia zapisanie punktu w sekwencji wyliczenia w celu powrotu do tego punktu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="a14e7-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="a14e7-112">Obiekt wywołujący musi zwolnić ten nowy moduł wyliczający niezależnie od pierwszego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a14e7-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
