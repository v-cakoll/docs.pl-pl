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
ms.openlocfilehash: ab1282109d7241c2599f8ca029fc79e4a3135209
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170996"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="06057-102">ISymUnmanagedConstant::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="06057-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="06057-103">Pobiera podpisu stałej.</span><span class="sxs-lookup"><span data-stu-id="06057-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06057-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06057-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06057-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06057-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="06057-106">[in] Długość buforu, `pcSig` parametr wskazuje.</span><span class="sxs-lookup"><span data-stu-id="06057-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="06057-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać podpis.</span><span class="sxs-lookup"><span data-stu-id="06057-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="06057-108">[out] Bufor, który przechowuje podpisu.</span><span class="sxs-lookup"><span data-stu-id="06057-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06057-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="06057-109">Return Value</span></span>  
 <span data-ttu-id="06057-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="06057-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06057-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06057-111">Requirements</span></span>  
 <span data-ttu-id="06057-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06057-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06057-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06057-113">See also</span></span>

- [<span data-ttu-id="06057-114">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="06057-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="06057-115">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="06057-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="06057-116">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="06057-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
