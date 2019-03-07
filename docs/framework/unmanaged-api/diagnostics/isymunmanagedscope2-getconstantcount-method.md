---
title: ISymUnmanagedScope2::GetConstantCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1dfc9ead6256ae700d5e619da4fae5745bdd759
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485161"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="99a45-102">ISymUnmanagedScope2::GetConstantCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="99a45-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="99a45-103">Pobiera liczbę stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="99a45-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99a45-104">Syntax</span></span>  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99a45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99a45-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="99a45-106">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać stałe.</span><span class="sxs-lookup"><span data-stu-id="99a45-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99a45-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99a45-107">Return Value</span></span>  
 <span data-ttu-id="99a45-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="99a45-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99a45-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99a45-109">Requirements</span></span>  
 <span data-ttu-id="99a45-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="99a45-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a45-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99a45-111">See also</span></span>
- [<span data-ttu-id="99a45-112">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="99a45-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
