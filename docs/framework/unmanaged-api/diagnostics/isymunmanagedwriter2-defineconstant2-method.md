---
title: ISymUnmanagedWriter2::DefineConstant2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e9bff5be747c4872554a69dd316de8ca9eb9934
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198936"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="fc899-102">ISymUnmanagedWriter2::DefineConstant2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc899-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="fc899-103">Definiuje nazwę wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="fc899-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc899-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc899-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc899-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc899-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fc899-106">[in] Nazwa stałe.</span><span class="sxs-lookup"><span data-stu-id="fc899-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="fc899-107">[in] Wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="fc899-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="fc899-108">[in] Token metadanych stałej.</span><span class="sxs-lookup"><span data-stu-id="fc899-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc899-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc899-109">Return Value</span></span>  
 <span data-ttu-id="fc899-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="fc899-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc899-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc899-111">Requirements</span></span>  
 <span data-ttu-id="fc899-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc899-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc899-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc899-113">See also</span></span>

- [<span data-ttu-id="fc899-114">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc899-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="fc899-115">DefineConstant, metoda</span><span class="sxs-lookup"><span data-stu-id="fc899-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
