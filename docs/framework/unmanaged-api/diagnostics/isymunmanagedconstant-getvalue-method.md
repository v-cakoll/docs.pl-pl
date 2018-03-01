---
title: "ISymUnmanagedConstant::GetValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15ae3e9f2e680c7e85d3b8daa0d6010773797258
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="77e97-102">ISymUnmanagedConstant::GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="77e97-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="77e97-103">Pobiera wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="77e97-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77e97-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77e97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77e97-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="77e97-106">[out] Wskaźnik do zmiennej, która otrzymuje wartość.</span><span class="sxs-lookup"><span data-stu-id="77e97-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77e97-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77e97-107">Return Value</span></span>  
 <span data-ttu-id="77e97-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="77e97-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e97-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77e97-109">Requirements</span></span>  
 <span data-ttu-id="77e97-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="77e97-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e97-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77e97-111">See Also</span></span>  
 [<span data-ttu-id="77e97-112">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="77e97-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="77e97-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="77e97-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="77e97-114">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="77e97-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
