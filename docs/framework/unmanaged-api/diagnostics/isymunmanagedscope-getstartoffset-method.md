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
ms.openlocfilehash: 19d116825efc4eb2ec1de22f232f46f8fb0fdf18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="34a9b-102">ISymUnmanagedScope::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="34a9b-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="34a9b-103">Pobiera Przesunięcie początkowe dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="34a9b-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34a9b-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34a9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34a9b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="34a9b-106">[out] Wskaźnik do `ULONG32` zawiera początkowe przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="34a9b-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34a9b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34a9b-107">Return Value</span></span>  
 <span data-ttu-id="34a9b-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="34a9b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34a9b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34a9b-109">Requirements</span></span>  
 <span data-ttu-id="34a9b-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="34a9b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a9b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34a9b-111">See Also</span></span>  
 [<span data-ttu-id="34a9b-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="34a9b-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="34a9b-113">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="34a9b-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
