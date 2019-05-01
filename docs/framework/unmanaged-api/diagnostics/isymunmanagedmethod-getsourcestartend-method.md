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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939558"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="124df-102">ISymUnmanagedMethod::GetSourceStartEnd — Metoda</span><span class="sxs-lookup"><span data-stu-id="124df-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="124df-103">Pobiera położenie dokumentu rozpoczęcia i zakończenia dla źródłowej, tej metody.</span><span class="sxs-lookup"><span data-stu-id="124df-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="124df-104">Na pierwszym miejscu tablicy jest początek, a na drugim miejscu tablicy jest zakończenia.</span><span class="sxs-lookup"><span data-stu-id="124df-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="124df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="124df-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="124df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="124df-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="124df-107">[in] Początkowe i końcowe dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="124df-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="124df-108">[in] Początkowe i końcowe wiersze w odpowiednich źródła dokumentów.</span><span class="sxs-lookup"><span data-stu-id="124df-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="124df-109">[in] Początkowy i końcowy kolumn w odpowiednich źródła dokumentów.</span><span class="sxs-lookup"><span data-stu-id="124df-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="124df-110">[out] `true` gdyby położenia zdefiniowanych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="124df-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="124df-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="124df-111">Return Value</span></span>  
 <span data-ttu-id="124df-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="124df-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="124df-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="124df-113">Requirements</span></span>  
 <span data-ttu-id="124df-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="124df-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124df-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="124df-115">See also</span></span>

- [<span data-ttu-id="124df-116">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="124df-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
