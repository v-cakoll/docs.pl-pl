---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod — Metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8efcd62f39a7de397ef93231fd125a17c7e513e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="2b1c4-102">ISymENCUnmanagedMethod::GetDocumentsForMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b1c4-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="2b1c4-103">Pobiera dokumentów, które ta metoda ma wiersze w.</span><span class="sxs-lookup"><span data-stu-id="2b1c4-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b1c4-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b1c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b1c4-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="2b1c4-106">[in] Długość buforu wskazywana przez `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="2b1c4-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="2b1c4-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w znaki buforu, muszą zawierać dokumenty.</span><span class="sxs-lookup"><span data-stu-id="2b1c4-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="2b1c4-108">[in] Buforu, który zawiera dokumenty.</span><span class="sxs-lookup"><span data-stu-id="2b1c4-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b1c4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b1c4-109">Return Value</span></span>  
 <span data-ttu-id="2b1c4-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2b1c4-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b1c4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b1c4-111">Requirements</span></span>  
 <span data-ttu-id="2b1c4-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2b1c4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b1c4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b1c4-113">See Also</span></span>  
 [<span data-ttu-id="2b1c4-114">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b1c4-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
