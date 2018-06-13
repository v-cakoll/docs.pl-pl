---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: b03d141f1d2bfc18428c2f8651a340b789cfb995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548558"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="6dddc-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="6dddc-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="6dddc-103">Powoduje, że moduł wyliczający, aby przejść dalej `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) nie zwróci tych elementów.</span><span class="sxs-lookup"><span data-stu-id="6dddc-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dddc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6dddc-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6dddc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dddc-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="6dddc-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="6dddc-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="6dddc-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="6dddc-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="6dddc-108">HRESULT: S_OK liczba elementów dostarczonych jest `celt`; W przeciwnym razie wartości S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="6dddc-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
