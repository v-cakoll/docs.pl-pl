---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: e3c0d7b8eeded403ce8391cff00ee18dccc38ed5
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441893"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="cfd99-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfd99-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="cfd99-103">Zobacz [DefineAsyncStepInfo —](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="cfd99-103">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd99-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfd99-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfd99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfd99-105">Parameters</span></span>  
  
|<span data-ttu-id="cfd99-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="cfd99-106">Parameter</span></span>|<span data-ttu-id="cfd99-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cfd99-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="cfd99-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cfd99-108">Return Value</span></span>  
 <span data-ttu-id="cfd99-109">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="cfd99-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd99-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfd99-110">Requirements</span></span>  
 <span data-ttu-id="cfd99-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cfd99-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd99-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfd99-112">See also</span></span>

- [<span data-ttu-id="cfd99-113">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cfd99-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
