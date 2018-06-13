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
ms.openlocfilehash: 3ae532b20ec3486fe56e2dff340a5ad89941a8df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424378"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="4200a-102">ISymUnmanagedConstant::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="4200a-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="4200a-103">Pobiera nazwę stałej.</span><span class="sxs-lookup"><span data-stu-id="4200a-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4200a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4200a-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4200a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4200a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4200a-106">[in] Długość buforu, który `szName` wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="4200a-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4200a-107">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazwę, takie jak zakończenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="4200a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="4200a-108">[out] Buforu, który przechowuje nazwę.</span><span class="sxs-lookup"><span data-stu-id="4200a-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4200a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4200a-109">Return Value</span></span>  
 <span data-ttu-id="4200a-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4200a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4200a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4200a-111">Requirements</span></span>  
 <span data-ttu-id="4200a-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4200a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4200a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4200a-113">See Also</span></span>  
 [<span data-ttu-id="4200a-114">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="4200a-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="4200a-115">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="4200a-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="4200a-116">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="4200a-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
