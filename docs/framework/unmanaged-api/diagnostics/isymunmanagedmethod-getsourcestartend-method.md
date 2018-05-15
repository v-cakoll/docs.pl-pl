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
ms.openlocfilehash: 1e15bab136540c73f8e1cff0e6bb52ec1d6c0063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="56229-102">ISymUnmanagedMethod::GetSourceStartEnd — Metoda</span><span class="sxs-lookup"><span data-stu-id="56229-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="56229-103">Pobiera dokument pozycje początkowe i końcowe dla źródła tej metody.</span><span class="sxs-lookup"><span data-stu-id="56229-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="56229-104">Pierwszą pozycję tablicy jest początek, a drugi tablicy znajdował się na końcu.</span><span class="sxs-lookup"><span data-stu-id="56229-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56229-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="56229-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56229-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="56229-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="56229-107">[in] Początkowa i końcowa dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="56229-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="56229-108">[in] Rozpoczęcia i zakończenia wierszy w odpowiednich źródła dokumentów.</span><span class="sxs-lookup"><span data-stu-id="56229-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="56229-109">[in] Początkowy i końcowy w odpowiadającej mu kolumny źródłowej dokumentów.</span><span class="sxs-lookup"><span data-stu-id="56229-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="56229-110">[out] `true` gdyby zdefiniowana; w przeciwnym razie wartość pozycji `false`.</span><span class="sxs-lookup"><span data-stu-id="56229-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56229-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56229-111">Return Value</span></span>  
 <span data-ttu-id="56229-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="56229-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56229-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56229-113">Requirements</span></span>  
 <span data-ttu-id="56229-114">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56229-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56229-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56229-115">See Also</span></span>  
 [<span data-ttu-id="56229-116">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="56229-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
