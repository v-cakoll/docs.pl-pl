---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f20039318d6e1230ccc0fbd203fc44686806bb2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604473"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="d434e-102">ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="d434e-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="d434e-103">Zobacz [DefineKickoffMethod, Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="d434e-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d434e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d434e-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d434e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d434e-105">Parameters</span></span>  
  
|<span data-ttu-id="d434e-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="d434e-106">Parameter</span></span>|<span data-ttu-id="d434e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d434e-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="d434e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d434e-108">Return Value</span></span>  
 <span data-ttu-id="d434e-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d434e-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d434e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d434e-110">Requirements</span></span>  
 <span data-ttu-id="d434e-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d434e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d434e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d434e-112">See also</span></span>
- [<span data-ttu-id="d434e-113">ISymUnmanagedAsyncMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="d434e-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
