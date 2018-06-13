---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3c7f7e06822f419282209ac39d4cbd46e600a66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424992"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="e3f0c-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3f0c-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="e3f0c-103">Pobiera liczbę dokumentów, które ta metoda ma wiersze w.</span><span class="sxs-lookup"><span data-stu-id="e3f0c-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3f0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3f0c-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3f0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3f0c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e3f0c-106">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać dokumenty.</span><span class="sxs-lookup"><span data-stu-id="e3f0c-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3f0c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3f0c-107">Return Value</span></span>  
 <span data-ttu-id="e3f0c-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e3f0c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3f0c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3f0c-109">Requirements</span></span>  
 <span data-ttu-id="e3f0c-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e3f0c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f0c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3f0c-111">See Also</span></span>  
 [<span data-ttu-id="e3f0c-112">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3f0c-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
