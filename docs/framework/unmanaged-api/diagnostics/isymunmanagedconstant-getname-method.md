---
title: "ISymUnmanagedConstant::GetName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d312329a2e59376c94937cf3d9bc08a8e6e0e862
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="d2ec2-102">ISymUnmanagedConstant::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2ec2-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="d2ec2-103">Pobiera nazwę stałej.</span><span class="sxs-lookup"><span data-stu-id="d2ec2-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ec2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2ec2-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2ec2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2ec2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d2ec2-106">[in] Długość buforu, który `szName` wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="d2ec2-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d2ec2-107">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazwę, takie jak zakończenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="d2ec2-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="d2ec2-108">[out] Buforu, który przechowuje nazwę.</span><span class="sxs-lookup"><span data-stu-id="d2ec2-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2ec2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2ec2-109">Return Value</span></span>  
 <span data-ttu-id="d2ec2-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d2ec2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2ec2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2ec2-111">Requirements</span></span>  
 <span data-ttu-id="d2ec2-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2ec2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ec2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2ec2-113">See Also</span></span>  
 [<span data-ttu-id="d2ec2-114">ISymUnmanagedConstant, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2ec2-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="d2ec2-115">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="d2ec2-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="d2ec2-116">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="d2ec2-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
