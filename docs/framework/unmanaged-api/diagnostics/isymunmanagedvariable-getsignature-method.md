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
ms.openlocfilehash: 2939d9cf3991a9e0b8f93bb301925b1092eca50e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446046"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="ccc7b-102">ISymUnmanagedVariable::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="ccc7b-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="ccc7b-103">Gets the signature of this variable.</span><span class="sxs-lookup"><span data-stu-id="ccc7b-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccc7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccc7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccc7b-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="ccc7b-106">[in] The length of the buffer pointed to by the `sig` parameter.</span><span class="sxs-lookup"><span data-stu-id="ccc7b-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="ccc7b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span><span class="sxs-lookup"><span data-stu-id="ccc7b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="ccc7b-108">[out] The buffer that stores the signature.</span><span class="sxs-lookup"><span data-stu-id="ccc7b-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccc7b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ccc7b-109">Return Value</span></span>  
 <span data-ttu-id="ccc7b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="ccc7b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc7b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ccc7b-111">Requirements</span></span>  
 <span data-ttu-id="ccc7b-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ccc7b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc7b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccc7b-113">See also</span></span>

- [<span data-ttu-id="ccc7b-114">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="ccc7b-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
