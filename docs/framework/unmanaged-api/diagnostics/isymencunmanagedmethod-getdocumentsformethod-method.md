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
ms.openlocfilehash: 89be772ee3d8a6fc5acb74d5ebe6d3c691764f89
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441958"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="3fa1c-102">ISymENCUnmanagedMethod::GetDocumentsForMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="3fa1c-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="3fa1c-103">Pobiera dokumenty, w których ta metoda zawiera wiersze.</span><span class="sxs-lookup"><span data-stu-id="3fa1c-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fa1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fa1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fa1c-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="3fa1c-106">podczas Długość buforu wskazywanego przez `pcDocs` .</span><span class="sxs-lookup"><span data-stu-id="3fa1c-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="3fa1c-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora wymaganego do przechowywania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="3fa1c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="3fa1c-108">podczas Bufor, który zawiera dokumenty.</span><span class="sxs-lookup"><span data-stu-id="3fa1c-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fa1c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3fa1c-109">Return Value</span></span>  
 <span data-ttu-id="3fa1c-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3fa1c-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fa1c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fa1c-111">Requirements</span></span>  
 <span data-ttu-id="3fa1c-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3fa1c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa1c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fa1c-113">See also</span></span>

- [<span data-ttu-id="3fa1c-114">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3fa1c-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
