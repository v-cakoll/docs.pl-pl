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
ms.openlocfilehash: b32865e0ac9d8a4a049db5d7ed6179879342c10a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778105"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="b12cc-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT — Metoda</span><span class="sxs-lookup"><span data-stu-id="b12cc-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="b12cc-103">Pobiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b12cc-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b12cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b12cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b12cc-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="b12cc-106">[out] Wskaźnik do HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b12cc-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b12cc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b12cc-107">Return Value</span></span>  
 <span data-ttu-id="b12cc-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="b12cc-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b12cc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b12cc-109">Requirements</span></span>  
 <span data-ttu-id="b12cc-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b12cc-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12cc-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b12cc-111">See also</span></span>

- [<span data-ttu-id="b12cc-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="b12cc-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
