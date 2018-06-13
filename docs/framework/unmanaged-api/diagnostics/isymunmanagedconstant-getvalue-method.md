---
title: ISymUnmanagedConstant::GetValue — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f51a41e8f00a0cf88b11078468ba5a8511fd1391
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424742"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="71e26-102">ISymUnmanagedConstant::GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="71e26-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="71e26-103">Pobiera wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="71e26-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e26-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71e26-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71e26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71e26-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="71e26-106">[out] Wskaźnik do zmiennej, która otrzymuje wartość.</span><span class="sxs-lookup"><span data-stu-id="71e26-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71e26-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="71e26-107">Return Value</span></span>  
 <span data-ttu-id="71e26-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="71e26-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71e26-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71e26-109">Requirements</span></span>  
 <span data-ttu-id="71e26-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="71e26-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e26-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71e26-111">See Also</span></span>  
 [<span data-ttu-id="71e26-112">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="71e26-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="71e26-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="71e26-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="71e26-114">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="71e26-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
