---
title: "ISymUnmanagedWriter::DefineField — Metoda"
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
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 51adddc6a8e58846ebefe3c130adaa670c8351e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="0cb9d-102">ISymUnmanagedWriter::DefineField — Metoda</span><span class="sxs-lookup"><span data-stu-id="0cb9d-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="0cb9d-103">Definiuje pojedynczą zmienną, która nie jest w metodzie.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="0cb9d-104">Ta metoda jest używana dla niektórych pól w klasach, pól bitowych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb9d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cb9d-105">Syntax</span></span>  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0cb9d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cb9d-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="0cb9d-107">[in] Typ metadanych lub metoda tokenu.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="0cb9d-108">[in] Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="0cb9d-109">[in] Atrybuty pól.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="0cb9d-110">[in] A `ULONG32` czyli rozmiar w znaki buforu, muszą zawierać podpis pola.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="0cb9d-111">[in] Tablica sygnatury pól.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="0cb9d-112">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="0cb9d-113">[in] Pierwszy adres specyfikacji pola.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="0cb9d-114">[in] Drugi adres specyfikacji pola.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="0cb9d-115">[in] Trzeci adres specyfikacji pola.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cb9d-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0cb9d-116">Return Value</span></span>  
 <span data-ttu-id="0cb9d-117">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0cb9d-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb9d-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0cb9d-118">Requirements</span></span>  
 <span data-ttu-id="0cb9d-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0cb9d-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb9d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cb9d-120">See Also</span></span>  
 [<span data-ttu-id="0cb9d-121">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="0cb9d-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
