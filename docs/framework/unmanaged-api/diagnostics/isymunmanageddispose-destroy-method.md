---
title: ISymUnmanagedDispose::Destroy — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51d2f0aedffdd88974a8184954ecbb9a231b70c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213681"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="be1f7-102">ISymUnmanagedDispose::Destroy — Metoda</span><span class="sxs-lookup"><span data-stu-id="be1f7-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="be1f7-103">Powoduje, że obiekt jest zwolnienie wszystkich odwołań wewnętrznego i zwraca błąd na dowolne wywołania metody kolejne.</span><span class="sxs-lookup"><span data-stu-id="be1f7-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be1f7-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="be1f7-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="be1f7-105">Return Value</span></span>  
 <span data-ttu-id="be1f7-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="be1f7-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be1f7-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be1f7-107">Requirements</span></span>  
 <span data-ttu-id="be1f7-108">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="be1f7-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1f7-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be1f7-109">See also</span></span>

- [<span data-ttu-id="be1f7-110">ISymUnmanagedDispose — Interfejs</span><span class="sxs-lookup"><span data-stu-id="be1f7-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
