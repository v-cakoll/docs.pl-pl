---
title: "ISymUnmanagedMethod::GetSourceStartEnd — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSourceStartEnd
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7b5e4fa5fcdb41126b827ee157230d79e07ed977
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="1cef0-102">ISymUnmanagedMethod::GetSourceStartEnd — Metoda</span><span class="sxs-lookup"><span data-stu-id="1cef0-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="1cef0-103">Pobiera dokument pozycje początkowe i końcowe dla źródła tej metody.</span><span class="sxs-lookup"><span data-stu-id="1cef0-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="1cef0-104">Pierwszą pozycję tablicy jest początek, a drugi tablicy znajdował się na końcu.</span><span class="sxs-lookup"><span data-stu-id="1cef0-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cef0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cef0-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cef0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cef0-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="1cef0-107">[in] Początkowa i końcowa dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1cef0-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="1cef0-108">[in] Rozpoczęcia i zakończenia wierszy w odpowiednich źródła dokumentów.</span><span class="sxs-lookup"><span data-stu-id="1cef0-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="1cef0-109">[in] Początkowy i końcowy w odpowiadającej mu kolumny źródłowej dokumentów.</span><span class="sxs-lookup"><span data-stu-id="1cef0-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1cef0-110">[out] `true` gdyby zdefiniowana; w przeciwnym razie wartość pozycji `false`.</span><span class="sxs-lookup"><span data-stu-id="1cef0-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cef0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1cef0-111">Return Value</span></span>  
 <span data-ttu-id="1cef0-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1cef0-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cef0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1cef0-113">Requirements</span></span>  
 <span data-ttu-id="1cef0-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1cef0-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cef0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1cef0-115">See Also</span></span>  
 [<span data-ttu-id="1cef0-116">ISymUnmanagedMethod — interfejs</span><span class="sxs-lookup"><span data-stu-id="1cef0-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
