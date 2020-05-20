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
ms.openlocfilehash: b8a3a74888a3caae03da6f88a003bd277939ae59
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615049"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="73438-102">ISymUnmanagedReader::GetDocuments — Metoda</span><span class="sxs-lookup"><span data-stu-id="73438-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="73438-103">Zwraca tablicę wszystkich dokumentów zdefiniowanych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="73438-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73438-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73438-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73438-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73438-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="73438-106">podczas Rozmiar `pDocs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="73438-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="73438-107">określoną Wskaźnik do zmiennej, która otrzymuje długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="73438-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="73438-108">określoną Wskaźnik do zmiennej, która otrzymuje tablicę dokumentu.</span><span class="sxs-lookup"><span data-stu-id="73438-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73438-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="73438-109">Return Value</span></span>  
 <span data-ttu-id="73438-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="73438-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73438-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73438-111">Requirements</span></span>  
 <span data-ttu-id="73438-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="73438-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73438-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73438-113">See also</span></span>

- [<span data-ttu-id="73438-114">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="73438-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
