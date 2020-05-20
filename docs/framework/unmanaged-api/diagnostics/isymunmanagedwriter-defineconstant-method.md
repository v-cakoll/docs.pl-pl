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
ms.openlocfilehash: 200e68abb3f176c267045bf2a5e7e35d18400519
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610096"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="9193d-102">ISymUnmanagedWriter::DefineConstant — Metoda</span><span class="sxs-lookup"><span data-stu-id="9193d-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="9193d-103">Definiuje nazwę wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="9193d-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9193d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9193d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9193d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9193d-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9193d-106">podczas Wskaźnik do elementu `WCHAR` , który definiuje stałą nazwę.</span><span class="sxs-lookup"><span data-stu-id="9193d-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="9193d-107">podczas Wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="9193d-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="9193d-108">podczas Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9193d-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="9193d-109">podczas Podpis typu dla stałej.</span><span class="sxs-lookup"><span data-stu-id="9193d-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9193d-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9193d-110">Return Value</span></span>  
 <span data-ttu-id="9193d-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9193d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9193d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9193d-112">Requirements</span></span>  
 <span data-ttu-id="9193d-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9193d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9193d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9193d-114">See also</span></span>

- [<span data-ttu-id="9193d-115">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9193d-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="9193d-116">DefineConstant2, metoda</span><span class="sxs-lookup"><span data-stu-id="9193d-116">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)
