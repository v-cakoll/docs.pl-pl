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
ms.openlocfilehash: 326f970f53293b74bbf8c5e77830f3f6ce1b73ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="a111f-102">ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="a111f-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="a111f-103">Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="a111f-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="a111f-104">W przeciwieństwie do niestandardowych atrybutów metadanych te atrybuty są przechowywane w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="a111f-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a111f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a111f-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a111f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a111f-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="a111f-107">[in] Token metadanych elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a111f-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="a111f-108">[in] Wskaźnik do `WCHAR` zawierający nazwę.</span><span class="sxs-lookup"><span data-stu-id="a111f-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="a111f-109">[in] A `ULONG32` wskazuje, że rozmiar `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a111f-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="a111f-110">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać atrybut bajtów.</span><span class="sxs-lookup"><span data-stu-id="a111f-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a111f-111">[out] Wskaźnik do buforu, który odbiera bajtów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a111f-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a111f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a111f-112">Return Value</span></span>  
 <span data-ttu-id="a111f-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a111f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a111f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a111f-114">Requirements</span></span>  
 <span data-ttu-id="a111f-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a111f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a111f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a111f-116">See Also</span></span>  
 [<span data-ttu-id="a111f-117">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a111f-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
