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
ms.openlocfilehash: 8ffcc3a079e7e9a9d69622dc6666bb0e7641d4e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155470"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="29d19-102">ISymUnmanagedWriter::SetSymAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="29d19-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="29d19-103">Określa atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="29d19-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="29d19-104">Te atrybuty są przechowywane w magazynie symboli, w przeciwieństwie do atrybutów niestandardowych metadanych.</span><span class="sxs-lookup"><span data-stu-id="29d19-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d19-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="29d19-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29d19-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="29d19-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="29d19-107">[in] Token metadanych, dla którego jest definiowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="29d19-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="29d19-108">[in] Wskaźnik do `WCHAR` zawierający nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="29d19-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="29d19-109">[in] A `ULONG32` oznacza rozmiar `data` tablicy.</span><span class="sxs-lookup"><span data-stu-id="29d19-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="29d19-110">[in] Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="29d19-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29d19-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29d19-111">Return Value</span></span>  
 <span data-ttu-id="29d19-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="29d19-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d19-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29d19-113">Requirements</span></span>  
 <span data-ttu-id="29d19-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29d19-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d19-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29d19-115">See also</span></span>

- [<span data-ttu-id="29d19-116">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="29d19-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
