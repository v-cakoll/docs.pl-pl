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
ms.openlocfilehash: 401dfbea0da309db24f3052f462daa66e8bbef4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449266"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="7ddb3-102">ISymUnmanagedConstant::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ddb3-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="7ddb3-103">Pobiera sygnaturę stałej.</span><span class="sxs-lookup"><span data-stu-id="7ddb3-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ddb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ddb3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ddb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ddb3-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="7ddb3-106">podczas Długość buforu, na który wskazuje parametr `pcSig`.</span><span class="sxs-lookup"><span data-stu-id="7ddb3-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="7ddb3-107">określoną Wskaźnik do `ULONG32`, który odbiera rozmiar (w znakach) bufora wymaganego do przechowywania podpisu.</span><span class="sxs-lookup"><span data-stu-id="7ddb3-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="7ddb3-108">określoną Bufor przechowujący podpis.</span><span class="sxs-lookup"><span data-stu-id="7ddb3-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ddb3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7ddb3-109">Return Value</span></span>  
 <span data-ttu-id="7ddb3-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7ddb3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ddb3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ddb3-111">Requirements</span></span>  
 <span data-ttu-id="7ddb3-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7ddb3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddb3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ddb3-113">See also</span></span>

- [<span data-ttu-id="7ddb3-114">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ddb3-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="7ddb3-115">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="7ddb3-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="7ddb3-116">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="7ddb3-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
