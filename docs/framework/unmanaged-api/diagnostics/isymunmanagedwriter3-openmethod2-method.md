---
title: ISymUnmanagedWriter3::OpenMethod2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b641f463eb9b664597b4806a6353278e8027d5b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709107"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="6c176-102">ISymUnmanagedWriter3::OpenMethod2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c176-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="6c176-103">Otwiera metody i zawiera przesunięcie rzeczywistych sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="6c176-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c176-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c176-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c176-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c176-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="6c176-106">[in] Token metadanych dla metody, które ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="6c176-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="6c176-107">[in] Przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="6c176-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="6c176-108">[in] Przesunięcie w obrazie.</span><span class="sxs-lookup"><span data-stu-id="6c176-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c176-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c176-109">Return Value</span></span>  
 <span data-ttu-id="6c176-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="6c176-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c176-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c176-111">Requirements</span></span>  
 <span data-ttu-id="6c176-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c176-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c176-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c176-113">See also</span></span>
- [<span data-ttu-id="6c176-114">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c176-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="6c176-115">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="6c176-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
