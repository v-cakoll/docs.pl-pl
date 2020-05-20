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
ms.openlocfilehash: d096101189d52401c407a4108c9c81e201d3f30d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441945"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="f0c74-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0c74-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="f0c74-103">Pobiera liczbę dokumentów, w których ta metoda zawiera wiersze.</span><span class="sxs-lookup"><span data-stu-id="f0c74-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0c74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0c74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0c74-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f0c74-106">określoną Wskaźnik do obiektu `ULONG32` , który odbiera rozmiar buforu wymaganego do przechowywania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="f0c74-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0c74-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f0c74-107">Return Value</span></span>  
 <span data-ttu-id="f0c74-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f0c74-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c74-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0c74-109">Requirements</span></span>  
 <span data-ttu-id="f0c74-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f0c74-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c74-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0c74-111">See also</span></span>

- [<span data-ttu-id="f0c74-112">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0c74-112">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
