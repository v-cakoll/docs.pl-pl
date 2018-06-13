---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a26ff1e0b1bb4d0de662f0186dc2f7958b9707f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425382"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="0b221-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b221-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="0b221-103">Zobacz [DefineAsyncStepInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="0b221-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b221-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b221-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b221-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b221-105">Parameters</span></span>  
  
|<span data-ttu-id="0b221-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="0b221-106">Parameter</span></span>|<span data-ttu-id="0b221-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0b221-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="0b221-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0b221-108">Return Value</span></span>  
 <span data-ttu-id="0b221-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0b221-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b221-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b221-110">Requirements</span></span>  
 <span data-ttu-id="0b221-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0b221-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b221-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b221-112">See Also</span></span>  
 [<span data-ttu-id="0b221-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b221-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
