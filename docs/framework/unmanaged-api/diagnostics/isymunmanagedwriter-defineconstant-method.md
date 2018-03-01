---
title: "ISymUnmanagedWriter::DefineConstant — Metoda"
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
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b22b0d9c9de27ba9950a0501193bc682586bfbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="d59fe-102">ISymUnmanagedWriter::DefineConstant — Metoda</span><span class="sxs-lookup"><span data-stu-id="d59fe-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="d59fe-103">Definiuje nazwę wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="d59fe-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d59fe-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d59fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d59fe-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d59fe-106">[in] Wskaźnik do `WCHAR` definiuje nazwę stałej.</span><span class="sxs-lookup"><span data-stu-id="d59fe-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="d59fe-107">[in] Wartość stała.</span><span class="sxs-lookup"><span data-stu-id="d59fe-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="d59fe-108">[in] Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d59fe-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="d59fe-109">[in] Podpis typu dla stałej.</span><span class="sxs-lookup"><span data-stu-id="d59fe-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59fe-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d59fe-110">Return Value</span></span>  
 <span data-ttu-id="d59fe-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d59fe-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59fe-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d59fe-112">Requirements</span></span>  
 <span data-ttu-id="d59fe-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d59fe-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59fe-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d59fe-114">See Also</span></span>  
 [<span data-ttu-id="d59fe-115">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="d59fe-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="d59fe-116">DefineConstant2, metoda</span><span class="sxs-lookup"><span data-stu-id="d59fe-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
