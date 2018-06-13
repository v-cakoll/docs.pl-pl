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
ms.openlocfilehash: ce9ce768e32434e0a1acd2fad67a0cdc99f49e18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430149"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="81402-102">ISymUnmanagedConstant::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="81402-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="81402-103">Pobiera podpisu stałej.</span><span class="sxs-lookup"><span data-stu-id="81402-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81402-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81402-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81402-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81402-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="81402-106">[in] Długość buforu, który `pcSig` wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="81402-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="81402-107">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera znakami muszą zawierać podpis buforu.</span><span class="sxs-lookup"><span data-stu-id="81402-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="81402-108">[out] Bufor, który przechowuje podpisu.</span><span class="sxs-lookup"><span data-stu-id="81402-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81402-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81402-109">Return Value</span></span>  
 <span data-ttu-id="81402-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="81402-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81402-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81402-111">Requirements</span></span>  
 <span data-ttu-id="81402-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="81402-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81402-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81402-113">See Also</span></span>  
 [<span data-ttu-id="81402-114">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="81402-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="81402-115">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="81402-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="81402-116">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="81402-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
