---
title: "ISymUnmanagedWriter::SetSymAttribute — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90360d6fe5a1a95719a9bb09e5e0b6b2a70675a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="70dc6-102">ISymUnmanagedWriter::SetSymAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="70dc6-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="70dc6-103">Definiuje atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="70dc6-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="70dc6-104">Te atrybuty są przechowywane w magazynie symboli, w przeciwieństwie do niestandardowych atrybutów metadanych.</span><span class="sxs-lookup"><span data-stu-id="70dc6-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70dc6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="70dc6-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70dc6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="70dc6-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="70dc6-107">[in] Token metadanych, dla których atrybut jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="70dc6-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="70dc6-108">[in] Wskaźnik do `WCHAR` zawierający nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="70dc6-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="70dc6-109">[in] A `ULONG32` wskazuje, że rozmiar `data` tablicy.</span><span class="sxs-lookup"><span data-stu-id="70dc6-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="70dc6-110">[in] Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="70dc6-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70dc6-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="70dc6-111">Return Value</span></span>  
 <span data-ttu-id="70dc6-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="70dc6-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70dc6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70dc6-113">Requirements</span></span>  
 <span data-ttu-id="70dc6-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="70dc6-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70dc6-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70dc6-115">See Also</span></span>  
 [<span data-ttu-id="70dc6-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="70dc6-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
