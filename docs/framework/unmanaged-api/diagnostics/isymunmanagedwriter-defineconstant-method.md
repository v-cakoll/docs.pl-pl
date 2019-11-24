---
title: ISymUnmanagedWriter::DefineConstant — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: c8d0145b9dffe1c0ff6ed3281c90f3bcec082ab8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428059"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="7cc90-102">ISymUnmanagedWriter::DefineConstant — Metoda</span><span class="sxs-lookup"><span data-stu-id="7cc90-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="7cc90-103">Defines a name for a constant value.</span><span class="sxs-lookup"><span data-stu-id="7cc90-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cc90-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cc90-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="7cc90-106">[in] A pointer to a `WCHAR` that defines the constant name.</span><span class="sxs-lookup"><span data-stu-id="7cc90-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="7cc90-107">[in] The value of the constant.</span><span class="sxs-lookup"><span data-stu-id="7cc90-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="7cc90-108">[in] The size of the `signature` array.</span><span class="sxs-lookup"><span data-stu-id="7cc90-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="7cc90-109">[in] The type signature for the constant.</span><span class="sxs-lookup"><span data-stu-id="7cc90-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cc90-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7cc90-110">Return Value</span></span>  
 <span data-ttu-id="7cc90-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="7cc90-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc90-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cc90-112">Requirements</span></span>  
 <span data-ttu-id="7cc90-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7cc90-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc90-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cc90-114">See also</span></span>

- [<span data-ttu-id="7cc90-115">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7cc90-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="7cc90-116">DefineConstant2, metoda</span><span class="sxs-lookup"><span data-stu-id="7cc90-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
