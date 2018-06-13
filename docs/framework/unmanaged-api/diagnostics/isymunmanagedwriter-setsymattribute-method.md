---
title: ISymUnmanagedWriter::SetSymAttribute — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1a55d4100d74b769b2bc1b8fe33d2042f5e739
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428304"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="27093-102">ISymUnmanagedWriter::SetSymAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="27093-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="27093-103">Definiuje atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="27093-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="27093-104">Te atrybuty są przechowywane w magazynie symboli, w przeciwieństwie do niestandardowych atrybutów metadanych.</span><span class="sxs-lookup"><span data-stu-id="27093-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27093-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="27093-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27093-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="27093-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="27093-107">[in] Token metadanych, dla których atrybut jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="27093-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="27093-108">[in] Wskaźnik do `WCHAR` zawierający nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="27093-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="27093-109">[in] A `ULONG32` wskazuje, że rozmiar `data` tablicy.</span><span class="sxs-lookup"><span data-stu-id="27093-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="27093-110">[in] Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="27093-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27093-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="27093-111">Return Value</span></span>  
 <span data-ttu-id="27093-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="27093-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27093-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27093-113">Requirements</span></span>  
 <span data-ttu-id="27093-114">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27093-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27093-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27093-115">See Also</span></span>  
 [<span data-ttu-id="27093-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="27093-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
