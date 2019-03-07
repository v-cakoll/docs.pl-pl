---
title: ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 258d6967d1586974a4258e7906fd71db6c461b07
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482187"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="d01b7-102">ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="d01b7-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="d01b7-103">Pobiera atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="d01b7-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="d01b7-104">W przeciwieństwie do metadanych atrybutów niestandardowych te atrybuty są przechowywane w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="d01b7-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d01b7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d01b7-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d01b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d01b7-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="d01b7-107">[in] Token metadanych elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d01b7-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="d01b7-108">[in] Wskaźnik do `WCHAR` zawierający nazwę.</span><span class="sxs-lookup"><span data-stu-id="d01b7-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="d01b7-109">[in] A `ULONG32` oznacza rozmiar `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d01b7-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="d01b7-110">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać bajtów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d01b7-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="d01b7-111">[out] Wskaźnik do buforu, który otrzymuje bajtów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d01b7-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d01b7-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d01b7-112">Return Value</span></span>  
 <span data-ttu-id="d01b7-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="d01b7-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d01b7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d01b7-114">Requirements</span></span>  
 <span data-ttu-id="d01b7-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d01b7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01b7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d01b7-116">See also</span></span>
- [<span data-ttu-id="d01b7-117">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d01b7-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
