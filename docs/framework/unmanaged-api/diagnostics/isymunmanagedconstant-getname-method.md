---
title: "ISymUnmanagedConstant::GetName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedConstant.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b6dc3eb79f351041687586327e4e095225acf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="ecbdb-102">ISymUnmanagedConstant::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecbdb-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="ecbdb-103">Pobiera nazwę stałej.</span><span class="sxs-lookup"><span data-stu-id="ecbdb-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecbdb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecbdb-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecbdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecbdb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ecbdb-106">[in] Długość buforu, który `szName` wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="ecbdb-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ecbdb-107">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazwę, takie jak zakończenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="ecbdb-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="ecbdb-108">[out] Buforu, który przechowuje nazwę.</span><span class="sxs-lookup"><span data-stu-id="ecbdb-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecbdb-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ecbdb-109">Return Value</span></span>  
 <span data-ttu-id="ecbdb-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ecbdb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecbdb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecbdb-111">Requirements</span></span>  
 <span data-ttu-id="ecbdb-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ecbdb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbdb-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecbdb-113">See Also</span></span>  
 [<span data-ttu-id="ecbdb-114">ISymUnmanagedConstant — interfejs</span><span class="sxs-lookup"><span data-stu-id="ecbdb-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="ecbdb-115">GetSignature — metoda</span><span class="sxs-lookup"><span data-stu-id="ecbdb-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="ecbdb-116">GetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="ecbdb-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
