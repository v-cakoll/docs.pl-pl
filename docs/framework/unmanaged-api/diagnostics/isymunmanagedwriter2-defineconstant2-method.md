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
ms.openlocfilehash: 70ee853ff657a75dcc4df1454c4354f9d3f8202f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614724"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="096b4-102">ISymUnmanagedWriter2::DefineConstant2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="096b4-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="096b4-103">Definiuje nazwę wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="096b4-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="096b4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="096b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="096b4-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="096b4-106">podczas Stała nazwa.</span><span class="sxs-lookup"><span data-stu-id="096b4-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="096b4-107">podczas Wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="096b4-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="096b4-108">podczas Token metadanych stałej.</span><span class="sxs-lookup"><span data-stu-id="096b4-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="096b4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="096b4-109">Return Value</span></span>  
 <span data-ttu-id="096b4-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="096b4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096b4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="096b4-111">Requirements</span></span>  
 <span data-ttu-id="096b4-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="096b4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="096b4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="096b4-113">See also</span></span>

- [<span data-ttu-id="096b4-114">ISymUnmanagedWriter2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="096b4-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="096b4-115">DefineConstant, metoda</span><span class="sxs-lookup"><span data-stu-id="096b4-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
