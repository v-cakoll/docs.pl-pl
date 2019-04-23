---
title: ISymUnmanagedConstant::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1da8d89cf9ae2eed7b846774434d6ea472afbb94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194399"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="33497-102">ISymUnmanagedConstant::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="33497-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="33497-103">Pobiera nazwę stałej.</span><span class="sxs-lookup"><span data-stu-id="33497-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33497-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33497-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33497-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33497-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="33497-106">[in] Długość buforu, `szName` parametr wskazuje.</span><span class="sxs-lookup"><span data-stu-id="33497-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="33497-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać nazwę, w tym zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="33497-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="33497-108">[out] Bufor, który przechowuje nazwę.</span><span class="sxs-lookup"><span data-stu-id="33497-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33497-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33497-109">Return Value</span></span>  
 <span data-ttu-id="33497-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="33497-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33497-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33497-111">Requirements</span></span>  
 <span data-ttu-id="33497-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="33497-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33497-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33497-113">See also</span></span>

- [<span data-ttu-id="33497-114">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="33497-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="33497-115">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="33497-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="33497-116">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="33497-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
