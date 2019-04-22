---
title: ISymUnmanagedScope2::GetConstants — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08bc85c7a5b53c145375ca34f11ec499e5e7528f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096826"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="9a32b-102">ISymUnmanagedScope2::GetConstants — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a32b-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="9a32b-103">Pobiera lokalne stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="9a32b-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a32b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a32b-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a32b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a32b-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="9a32b-106">[in] Długość buforu, `pcConstants` parametr wskazuje.</span><span class="sxs-lookup"><span data-stu-id="9a32b-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="9a32b-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać stałe.</span><span class="sxs-lookup"><span data-stu-id="9a32b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="9a32b-108">[out] Bufor, który przechowuje stałych.</span><span class="sxs-lookup"><span data-stu-id="9a32b-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a32b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9a32b-109">Return Value</span></span>  
 <span data-ttu-id="9a32b-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="9a32b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a32b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a32b-111">Requirements</span></span>  
 <span data-ttu-id="9a32b-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9a32b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a32b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a32b-113">See also</span></span>

- [<span data-ttu-id="9a32b-114">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a32b-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
