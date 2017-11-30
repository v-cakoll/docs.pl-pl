---
title: "ISymUnmanagedReader::GetSymAttribute — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f57d2c4541945d90b1695850311928884fdc9cc5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="048e1-102">ISymUnmanagedReader::GetSymAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="048e1-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="048e1-103">Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="048e1-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="048e1-104">W przeciwieństwie do niestandardowych atrybutów metadanych te atrybuty niestandardowe są przechowywane w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="048e1-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048e1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="048e1-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="048e1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="048e1-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="048e1-107">[in] Token metadanych dla obiektu, dla którego wymagany jest atrybut.</span><span class="sxs-lookup"><span data-stu-id="048e1-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="048e1-108">[in] Wskaźnik do zmiennej, która wskazuje atrybut do pobrania.</span><span class="sxs-lookup"><span data-stu-id="048e1-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="048e1-109">[in] Rozmiar `buffer` tablicy.</span><span class="sxs-lookup"><span data-stu-id="048e1-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="048e1-110">[out] Wskaźnik do zmiennej, która odbiera długość danych atrybutu.</span><span class="sxs-lookup"><span data-stu-id="048e1-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="048e1-111">[out] Wskaźnik do zmiennej, która odbiera dane atrybutu.</span><span class="sxs-lookup"><span data-stu-id="048e1-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="048e1-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="048e1-112">Return Value</span></span>  
 <span data-ttu-id="048e1-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="048e1-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="048e1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="048e1-114">Requirements</span></span>  
 <span data-ttu-id="048e1-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="048e1-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048e1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="048e1-116">See Also</span></span>  
 [<span data-ttu-id="048e1-117">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="048e1-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
