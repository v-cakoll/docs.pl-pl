---
title: IEnumRAWINPUTDEVIC:Skip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e232d2525f9dfa339516f766d417ea9c3ee976c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="d7c37-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="d7c37-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="d7c37-103">Powoduje, że moduł wyliczający, aby przejść dalej `celt` elementów w wyliczeniu, aby następne wywołanie [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) nie zwróci tych elementów.</span><span class="sxs-lookup"><span data-stu-id="d7c37-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7c37-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7c37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7c37-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="d7c37-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="d7c37-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d7c37-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="d7c37-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="d7c37-108">HRESULT: S_OK liczba elementów dostarczonych jest `celt`; W przeciwnym razie wartości S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="d7c37-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
