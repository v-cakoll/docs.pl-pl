---
title: "ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f999e8cfba38ff4b4b15baea7ca9fa89606cb0ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="08262-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="08262-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="08262-103">Zobacz [DefineAsyncStepInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="08262-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08262-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08262-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08262-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08262-105">Parameters</span></span>  
  
|<span data-ttu-id="08262-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="08262-106">Parameter</span></span>|<span data-ttu-id="08262-107">Opis</span><span class="sxs-lookup"><span data-stu-id="08262-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="08262-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="08262-108">Return Value</span></span>  
 <span data-ttu-id="08262-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="08262-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08262-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08262-110">Requirements</span></span>  
 <span data-ttu-id="08262-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="08262-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08262-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08262-112">See Also</span></span>  
 [<span data-ttu-id="08262-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="08262-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
