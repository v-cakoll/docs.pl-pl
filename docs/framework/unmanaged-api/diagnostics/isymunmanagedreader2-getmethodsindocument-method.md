---
title: ISymUnmanagedReader2::GetMethodsInDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7fa192a8e8b8a876f672e36bb906a714b1266e2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736664"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="4ce62-102">ISymUnmanagedReader2::GetMethodsInDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ce62-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="4ce62-103">Pobiera każdej metody, która ma informacje wiersza w podany dokument.</span><span class="sxs-lookup"><span data-stu-id="4ce62-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ce62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ce62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ce62-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="4ce62-106">[in] Wskaźnik do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4ce62-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="4ce62-107">[in] A `ULONG32` oznacza rozmiar `pRetVal` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4ce62-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="4ce62-108">[out] Wskaźnik do `ULONG32` rozmiar buforu, muszą zawierać metody, która otrzymuje.</span><span class="sxs-lookup"><span data-stu-id="4ce62-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4ce62-109">[out] Wskaźnik do buforu, który otrzymuje te metody.</span><span class="sxs-lookup"><span data-stu-id="4ce62-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ce62-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ce62-110">Return Value</span></span>  
 <span data-ttu-id="4ce62-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="4ce62-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ce62-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ce62-112">Requirements</span></span>  
 <span data-ttu-id="4ce62-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4ce62-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce62-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ce62-114">See also</span></span>

- [<span data-ttu-id="4ce62-115">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ce62-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
