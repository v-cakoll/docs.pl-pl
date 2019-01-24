---
title: ISymUnmanagedReader::GetDocuments — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68f2cc471a33d2c0ea92ceab59d5ba9ecb86e7f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509590"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="b4dff-102">ISymUnmanagedReader::GetDocuments — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4dff-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="b4dff-103">Zwraca tablicę wszystkich dokumentów, które są zdefiniowane w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="b4dff-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4dff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4dff-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4dff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4dff-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="b4dff-106">[in] Rozmiar `pDocs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b4dff-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="b4dff-107">[out] Wskaźnik do zmiennej, która odbiera długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="b4dff-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="b4dff-108">[out] Wskaźnik do zmiennej, która odbiera tablicy dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b4dff-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4dff-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b4dff-109">Return Value</span></span>  
 <span data-ttu-id="b4dff-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="b4dff-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4dff-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4dff-111">Requirements</span></span>  
 <span data-ttu-id="b4dff-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4dff-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4dff-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4dff-113">See also</span></span>
- [<span data-ttu-id="b4dff-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4dff-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
