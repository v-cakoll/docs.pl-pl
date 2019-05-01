---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7c72d0766580f9aa3aa678aacd872b804172a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940221"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="33090-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="33090-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="33090-103">Zobacz [DefineAsyncStepInfo, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="33090-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33090-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33090-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33090-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33090-105">Parameters</span></span>  
  
|<span data-ttu-id="33090-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="33090-106">Parameter</span></span>|<span data-ttu-id="33090-107">Opis</span><span class="sxs-lookup"><span data-stu-id="33090-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="33090-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33090-108">Return Value</span></span>  
 <span data-ttu-id="33090-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="33090-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33090-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33090-110">Requirements</span></span>  
 <span data-ttu-id="33090-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33090-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33090-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33090-112">See also</span></span>

- [<span data-ttu-id="33090-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="33090-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
