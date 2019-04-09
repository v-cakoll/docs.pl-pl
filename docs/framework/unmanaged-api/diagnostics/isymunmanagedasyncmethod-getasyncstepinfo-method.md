---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7c72d0766580f9aa3aa678aacd872b804172a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131433"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="32e9d-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="32e9d-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="32e9d-103">Zobacz [DefineAsyncStepInfo, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="32e9d-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32e9d-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32e9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32e9d-105">Parameters</span></span>  
  
|<span data-ttu-id="32e9d-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="32e9d-106">Parameter</span></span>|<span data-ttu-id="32e9d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="32e9d-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="32e9d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32e9d-108">Return Value</span></span>  
 <span data-ttu-id="32e9d-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="32e9d-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32e9d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32e9d-110">Requirements</span></span>  
 <span data-ttu-id="32e9d-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="32e9d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e9d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32e9d-112">See also</span></span>

- [<span data-ttu-id="32e9d-113">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="32e9d-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
