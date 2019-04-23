---
title: ISymUnmanagedScope::GetStartOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: faab55199a3b921ea8b995e2a0f9823fb4da9cc7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230593"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="24e77-102">ISymUnmanagedScope::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="24e77-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="24e77-103">Pobiera Przesunięcie początkowe dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="24e77-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24e77-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24e77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24e77-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="24e77-106">[out] Wskaźnik do `ULONG32` zawierający Przesunięcie początkowe.</span><span class="sxs-lookup"><span data-stu-id="24e77-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24e77-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24e77-107">Return Value</span></span>  
 <span data-ttu-id="24e77-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="24e77-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e77-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24e77-109">Requirements</span></span>  
 <span data-ttu-id="24e77-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="24e77-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e77-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24e77-111">See also</span></span>

- [<span data-ttu-id="24e77-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="24e77-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="24e77-113">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="24e77-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
