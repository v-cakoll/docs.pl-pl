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
ms.openlocfilehash: 1534955c1f7cfd37732a08b0b33cda5bff8a8aab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638622"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="bb64b-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb64b-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="bb64b-103">Pobiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bb64b-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb64b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb64b-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb64b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb64b-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="bb64b-106">[out] Wskaźnik do HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bb64b-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb64b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb64b-107">Return Value</span></span>  
 <span data-ttu-id="bb64b-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="bb64b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb64b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb64b-109">Requirements</span></span>  
 <span data-ttu-id="bb64b-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bb64b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb64b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb64b-111">See also</span></span>

- [<span data-ttu-id="bb64b-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb64b-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
