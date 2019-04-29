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
ms.openlocfilehash: a3dcb1327ad50761a8268e8adc7b1e976cae0b3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650690"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="6edb6-102">ISymUnmanagedWriter3::OpenMethod2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="6edb6-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="6edb6-103">Otwiera metody i zawiera przesunięcie rzeczywistych sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="6edb6-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edb6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6edb6-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6edb6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6edb6-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="6edb6-106">[in] Token metadanych dla metody, które ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="6edb6-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="6edb6-107">[in] Przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="6edb6-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="6edb6-108">[in] Przesunięcie w obrazie.</span><span class="sxs-lookup"><span data-stu-id="6edb6-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6edb6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6edb6-109">Return Value</span></span>  
 <span data-ttu-id="6edb6-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="6edb6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edb6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6edb6-111">Requirements</span></span>  
 <span data-ttu-id="6edb6-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6edb6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edb6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6edb6-113">See also</span></span>

- [<span data-ttu-id="6edb6-114">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6edb6-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="6edb6-115">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="6edb6-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
