---
title: ISymUnmanagedMethod::GetSourceStartEnd — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d32e3ac0ff3179a9bb32f82e5ca33fd89c4ec410
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151193"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="3806f-102">ISymUnmanagedMethod::GetSourceStartEnd — Metoda</span><span class="sxs-lookup"><span data-stu-id="3806f-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="3806f-103">Pobiera położenie dokumentu rozpoczęcia i zakończenia dla źródłowej, tej metody.</span><span class="sxs-lookup"><span data-stu-id="3806f-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="3806f-104">Na pierwszym miejscu tablicy jest początek, a na drugim miejscu tablicy jest zakończenia.</span><span class="sxs-lookup"><span data-stu-id="3806f-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3806f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3806f-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3806f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3806f-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="3806f-107">[in] Początkowe i końcowe dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3806f-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="3806f-108">[in] Początkowe i końcowe wiersze w odpowiednich źródła dokumentów.</span><span class="sxs-lookup"><span data-stu-id="3806f-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="3806f-109">[in] Początkowy i końcowy kolumn w odpowiednich źródła dokumentów.</span><span class="sxs-lookup"><span data-stu-id="3806f-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3806f-110">[out] `true` gdyby położenia zdefiniowanych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3806f-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3806f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3806f-111">Return Value</span></span>  
 <span data-ttu-id="3806f-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="3806f-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3806f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3806f-113">Requirements</span></span>  
 <span data-ttu-id="3806f-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3806f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3806f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3806f-115">See also</span></span>

- [<span data-ttu-id="3806f-116">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3806f-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
