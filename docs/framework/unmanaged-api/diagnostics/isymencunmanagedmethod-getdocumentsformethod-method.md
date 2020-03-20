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
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176633"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="367b4-102">ISymENCUnmanagedMethod::GetDocumentsForMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="367b4-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="367b4-103">Pobiera dokumenty, w których ta metoda ma wiersze.</span><span class="sxs-lookup"><span data-stu-id="367b4-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="367b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="367b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="367b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="367b4-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="367b4-106">[w] Długość buforu wskazana `pcDocs`przez .</span><span class="sxs-lookup"><span data-stu-id="367b4-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="367b4-107">[na zewnątrz] Wskaźnik do, `ULONG32` który odbiera rozmiar, w znakach, buforu wymagane do przechowywania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="367b4-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="367b4-108">[w] Bufor, który zawiera dokumenty.</span><span class="sxs-lookup"><span data-stu-id="367b4-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="367b4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="367b4-109">Return Value</span></span>  
 <span data-ttu-id="367b4-110">S_OK, jeśli metoda powiedzie się; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="367b4-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="367b4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="367b4-111">Requirements</span></span>  
 <span data-ttu-id="367b4-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="367b4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367b4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="367b4-113">See also</span></span>

- [<span data-ttu-id="367b4-114">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="367b4-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
