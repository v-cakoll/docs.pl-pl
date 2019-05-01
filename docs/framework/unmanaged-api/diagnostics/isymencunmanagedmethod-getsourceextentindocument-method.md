---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 442584cffe4b4ae44702892587e261d41abf4e8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940247"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="22dbb-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="22dbb-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="22dbb-103">Pobiera najmniejszą liczbę linii i uruchomić największy wiersz końcowy w metodzie w określonym dokumentem.</span><span class="sxs-lookup"><span data-stu-id="22dbb-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22dbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22dbb-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22dbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22dbb-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="22dbb-106">[in] Wskaźnik do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22dbb-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="22dbb-107">[out] Wskaźnik do `ULONG32` odbierająca wiersza rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="22dbb-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="22dbb-108">[out] Wskaźnik do `ULONG32` odbierająca zakończyć wiersza.</span><span class="sxs-lookup"><span data-stu-id="22dbb-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22dbb-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="22dbb-109">Return Value</span></span>  
 <span data-ttu-id="22dbb-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="22dbb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22dbb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22dbb-111">Requirements</span></span>  
 <span data-ttu-id="22dbb-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="22dbb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22dbb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22dbb-113">See also</span></span>

- [<span data-ttu-id="22dbb-114">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="22dbb-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
