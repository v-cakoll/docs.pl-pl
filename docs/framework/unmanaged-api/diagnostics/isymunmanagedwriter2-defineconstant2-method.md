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
ms.openlocfilehash: 6600ca7e70ac77ffba0c75812f27d388c354ece6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438318"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="94d37-102">ISymUnmanagedWriter2::DefineConstant2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="94d37-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="94d37-103">Defines a name for a constant value.</span><span class="sxs-lookup"><span data-stu-id="94d37-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94d37-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94d37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94d37-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="94d37-106">[in] The constant name.</span><span class="sxs-lookup"><span data-stu-id="94d37-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="94d37-107">[in] The value of the constant.</span><span class="sxs-lookup"><span data-stu-id="94d37-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="94d37-108">[in] The metadata token of the constant.</span><span class="sxs-lookup"><span data-stu-id="94d37-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94d37-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="94d37-109">Return Value</span></span>  
 <span data-ttu-id="94d37-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="94d37-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94d37-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94d37-111">Requirements</span></span>  
 <span data-ttu-id="94d37-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94d37-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d37-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94d37-113">See also</span></span>

- [<span data-ttu-id="94d37-114">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="94d37-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="94d37-115">DefineConstant, metoda</span><span class="sxs-lookup"><span data-stu-id="94d37-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
