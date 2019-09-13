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
ms.openlocfilehash: 4450c262b75a73114cb7de7de98567f053bbf564
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894465"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="9508d-102">ISymUnmanagedWriter::SetSymAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="9508d-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="9508d-103">Definiuje atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="9508d-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="9508d-104">Te atrybuty są przechowywane w magazynie symboli, w przeciwieństwie do atrybutów niestandardowych metadanych.</span><span class="sxs-lookup"><span data-stu-id="9508d-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9508d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9508d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9508d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9508d-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="9508d-107">podczas Token metadanych, dla którego atrybut jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="9508d-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="9508d-108">podczas Wskaźnik do elementu `WCHAR` , który zawiera nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9508d-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="9508d-109">podczas `ULONG32` Wskazuje rozmiar`data` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9508d-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="9508d-110">podczas Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9508d-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9508d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9508d-111">Return Value</span></span>  
 <span data-ttu-id="9508d-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie, E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9508d-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9508d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9508d-113">Requirements</span></span>  
 <span data-ttu-id="9508d-114">**Nagłówki** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9508d-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9508d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9508d-115">See also</span></span>

- [<span data-ttu-id="9508d-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="9508d-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
