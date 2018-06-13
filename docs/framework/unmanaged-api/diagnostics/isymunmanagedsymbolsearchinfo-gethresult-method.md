---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 775f5a2129a635c79a48d5218d5eb91ee83ee779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427886"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="6ad0d-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ad0d-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="6ad0d-103">Pobiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6ad0d-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ad0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ad0d-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ad0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ad0d-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="6ad0d-106">[out] Wskaźnik do HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6ad0d-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ad0d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ad0d-107">Return Value</span></span>  
 <span data-ttu-id="6ad0d-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6ad0d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ad0d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ad0d-109">Requirements</span></span>  
 <span data-ttu-id="6ad0d-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ad0d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad0d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ad0d-111">See Also</span></span>  
 [<span data-ttu-id="6ad0d-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ad0d-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
