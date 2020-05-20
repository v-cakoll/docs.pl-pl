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
ms.openlocfilehash: 9dcd8282adf200932e86c950bee0b073780ce02d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615309"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="2a675-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a675-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="2a675-103">Pobiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2a675-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a675-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a675-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a675-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a675-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="2a675-106">określoną Wskaźnik do HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2a675-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a675-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2a675-107">Return Value</span></span>  
 <span data-ttu-id="2a675-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2a675-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a675-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a675-109">Requirements</span></span>  
 <span data-ttu-id="2a675-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2a675-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a675-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a675-111">See also</span></span>

- [<span data-ttu-id="2a675-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a675-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
