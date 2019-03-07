---
title: ISymUnmanagedConstant::GetSignature — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb893f06a5e905b981a408887f1c6bf5718ea79a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498565"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="bc574-102">ISymUnmanagedConstant::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc574-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="bc574-103">Pobiera podpisu stałej.</span><span class="sxs-lookup"><span data-stu-id="bc574-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc574-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc574-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc574-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc574-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="bc574-106">[in] Długość buforu, `pcSig` parametr wskazuje.</span><span class="sxs-lookup"><span data-stu-id="bc574-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="bc574-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać podpis.</span><span class="sxs-lookup"><span data-stu-id="bc574-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="bc574-108">[out] Bufor, który przechowuje podpisu.</span><span class="sxs-lookup"><span data-stu-id="bc574-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc574-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bc574-109">Return Value</span></span>  
 <span data-ttu-id="bc574-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="bc574-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc574-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc574-111">Requirements</span></span>  
 <span data-ttu-id="bc574-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bc574-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc574-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc574-113">See also</span></span>
- [<span data-ttu-id="bc574-114">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc574-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="bc574-115">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="bc574-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="bc574-116">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="bc574-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
