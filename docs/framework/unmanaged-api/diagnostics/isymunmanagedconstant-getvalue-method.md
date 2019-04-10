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
ms.openlocfilehash: 75cc16f44ddf29b161c758718b697cc2aaba8e08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204669"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="7370a-102">ISymUnmanagedConstant::GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="7370a-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="7370a-103">Pobiera wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="7370a-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7370a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7370a-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7370a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7370a-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="7370a-106">[out] Wskaźnik do zmiennej, która otrzymuje wartość.</span><span class="sxs-lookup"><span data-stu-id="7370a-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7370a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7370a-107">Return Value</span></span>  
 <span data-ttu-id="7370a-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="7370a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7370a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7370a-109">Requirements</span></span>  
 <span data-ttu-id="7370a-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7370a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7370a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7370a-111">See also</span></span>

- [<span data-ttu-id="7370a-112">ISymUnmanagedConstant — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7370a-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="7370a-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="7370a-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="7370a-114">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="7370a-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
