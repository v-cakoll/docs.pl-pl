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
ms.openlocfilehash: ef1b8dce5c84382a9039787d2205f1ac8ccbc5bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166468"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="7a17b-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a17b-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="7a17b-103">Pobiera liczbę dokumentów, które ta metoda powoduje wierszy.</span><span class="sxs-lookup"><span data-stu-id="7a17b-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a17b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a17b-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a17b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a17b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7a17b-106">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać dokumentów.</span><span class="sxs-lookup"><span data-stu-id="7a17b-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a17b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7a17b-107">Return Value</span></span>  
 <span data-ttu-id="7a17b-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="7a17b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a17b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a17b-109">Requirements</span></span>  
 <span data-ttu-id="7a17b-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a17b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a17b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a17b-111">See also</span></span>

- [<span data-ttu-id="7a17b-112">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a17b-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
