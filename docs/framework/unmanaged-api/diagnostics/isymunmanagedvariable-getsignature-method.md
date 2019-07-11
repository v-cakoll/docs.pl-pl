---
title: ISymUnmanagedVariable::GetSignature — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abd4bb00f5c1e703740462f1709407616ac8a8e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778244"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="28de2-102">ISymUnmanagedVariable::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="28de2-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="28de2-103">Pobiera podpis tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="28de2-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28de2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28de2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28de2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28de2-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="28de2-106">[in] Długość buforu wskazywany przez `sig` parametru.</span><span class="sxs-lookup"><span data-stu-id="28de2-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="28de2-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać podpis.</span><span class="sxs-lookup"><span data-stu-id="28de2-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="28de2-108">[out] Bufor, który przechowuje podpisu.</span><span class="sxs-lookup"><span data-stu-id="28de2-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28de2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="28de2-109">Return Value</span></span>  
 <span data-ttu-id="28de2-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="28de2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28de2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28de2-111">Requirements</span></span>  
 <span data-ttu-id="28de2-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28de2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28de2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28de2-113">See also</span></span>

- [<span data-ttu-id="28de2-114">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="28de2-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
