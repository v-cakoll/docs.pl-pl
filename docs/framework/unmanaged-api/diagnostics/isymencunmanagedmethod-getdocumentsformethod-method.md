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
ms.openlocfilehash: cd294037774721839b0c4f1f09bdc2a6e3b87841
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562677"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="d3615-102">ISymENCUnmanagedMethod::GetDocumentsForMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3615-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="d3615-103">Pobiera dokumentów, dla których ta metoda powoduje wierszy.</span><span class="sxs-lookup"><span data-stu-id="d3615-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3615-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3615-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3615-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3615-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="d3615-106">[in] Długość buforu wskazywany przez `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="d3615-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="d3615-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać dokumentów.</span><span class="sxs-lookup"><span data-stu-id="d3615-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="d3615-108">[in] Bufor, który zawiera dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d3615-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3615-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3615-109">Return Value</span></span>  
 <span data-ttu-id="d3615-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d3615-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3615-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3615-111">Requirements</span></span>  
 <span data-ttu-id="d3615-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d3615-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3615-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3615-113">See also</span></span>
- [<span data-ttu-id="d3615-114">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3615-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
