---
title: ISymUnmanagedWriter::DefineField — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fd9798b3681d66e71d5703f4d16564b153da07b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176179"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="32ed8-102">ISymUnmanagedWriter::DefineField — Metoda</span><span class="sxs-lookup"><span data-stu-id="32ed8-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="32ed8-103">Definiuje pojedynczej zmiennej, która nie znajduje się w metody.</span><span class="sxs-lookup"><span data-stu-id="32ed8-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="32ed8-104">Ta metoda jest używana w przypadku niektórych pól w klasach, pola bitowe i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="32ed8-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ed8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="32ed8-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="32ed8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="32ed8-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="32ed8-107">[in] Typ metadanych lub metoda tokenu.</span><span class="sxs-lookup"><span data-stu-id="32ed8-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="32ed8-108">[in] Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="32ed8-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="32ed8-109">[in] Atrybuty pól.</span><span class="sxs-lookup"><span data-stu-id="32ed8-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="32ed8-110">[in] A `ULONG32` oznacza to rozmiar, w postaci, buforu, muszą zawierać podpis pola.</span><span class="sxs-lookup"><span data-stu-id="32ed8-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="32ed8-111">[in] Tablica sygnatury pól.</span><span class="sxs-lookup"><span data-stu-id="32ed8-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="32ed8-112">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="32ed8-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="32ed8-113">[in] Pierwszy adres dotyczyło pola.</span><span class="sxs-lookup"><span data-stu-id="32ed8-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="32ed8-114">[in] Drugi adres dotyczyło pola.</span><span class="sxs-lookup"><span data-stu-id="32ed8-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="32ed8-115">[in] Trzeci adres dotyczyło pola.</span><span class="sxs-lookup"><span data-stu-id="32ed8-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32ed8-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32ed8-116">Return Value</span></span>  
 <span data-ttu-id="32ed8-117">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="32ed8-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ed8-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32ed8-118">Requirements</span></span>  
 <span data-ttu-id="32ed8-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="32ed8-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ed8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32ed8-120">See also</span></span>

- [<span data-ttu-id="32ed8-121">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="32ed8-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
