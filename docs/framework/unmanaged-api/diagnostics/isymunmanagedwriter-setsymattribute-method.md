---
title: "ISymUnmanagedWriter::SetSymAttribute — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c59c3c8ec4534f0a7587d4fdb772683715363066
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="d5c49-102">ISymUnmanagedWriter::SetSymAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="d5c49-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="d5c49-103">Definiuje atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="d5c49-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="d5c49-104">Te atrybuty są przechowywane w magazynie symboli, w przeciwieństwie do niestandardowych atrybutów metadanych.</span><span class="sxs-lookup"><span data-stu-id="d5c49-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c49-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5c49-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5c49-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5c49-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="d5c49-107">[in] Token metadanych, dla których atrybut jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d5c49-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="d5c49-108">[in] Wskaźnik do `WCHAR` zawierający nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d5c49-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="d5c49-109">[in] A `ULONG32` wskazuje, że rozmiar `data` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d5c49-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="d5c49-110">[in] Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d5c49-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5c49-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d5c49-111">Return Value</span></span>  
 <span data-ttu-id="d5c49-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d5c49-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c49-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5c49-113">Requirements</span></span>  
 <span data-ttu-id="d5c49-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d5c49-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c49-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5c49-115">See Also</span></span>  
 [<span data-ttu-id="d5c49-116">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="d5c49-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
