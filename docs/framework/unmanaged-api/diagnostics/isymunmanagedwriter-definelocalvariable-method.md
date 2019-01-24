---
title: ISymUnmanagedWriter::DefineLocalVariable — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c62ad58cd7ad1bd752d5958a5630dc7a019131e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645447"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="ff96b-102">ISymUnmanagedWriter::DefineLocalVariable — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff96b-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="ff96b-103">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="ff96b-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="ff96b-104">Tę metodę można wywoływać wielokrotnie dla zmiennej o tej samej nazwie, który ma wiele domów w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ff96b-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="ff96b-105">W takim jednak wartości `startOffset` i `endOffset` parametry nie mogą się nakładać.</span><span class="sxs-lookup"><span data-stu-id="ff96b-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff96b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff96b-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff96b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff96b-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ff96b-108">[in] Wskaźnik do `WCHAR` definiujący lokalna nazwa zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ff96b-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="ff96b-109">[in] Lokalne atrybuty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ff96b-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="ff96b-110">[in] A `ULONG32` rozmiar w bajtach, który wskazuje z `signature` buforu.</span><span class="sxs-lookup"><span data-stu-id="ff96b-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="ff96b-111">[in] Sygnatura lokalna zmienna.</span><span class="sxs-lookup"><span data-stu-id="ff96b-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="ff96b-112">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="ff96b-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="ff96b-113">[in] Pierwszy adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="ff96b-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="ff96b-114">[in] Drugi adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="ff96b-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="ff96b-115">[in] Trzeci adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="ff96b-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="ff96b-116">[in] Przesunięcie początku dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ff96b-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="ff96b-117">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ff96b-117">This parameter is optional.</span></span> <span data-ttu-id="ff96b-118">Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres.</span><span class="sxs-lookup"><span data-stu-id="ff96b-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="ff96b-119">Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="ff96b-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="ff96b-120">[in] Przesunięcie zakończenia dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ff96b-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="ff96b-121">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ff96b-121">This parameter is optional.</span></span> <span data-ttu-id="ff96b-122">Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres.</span><span class="sxs-lookup"><span data-stu-id="ff96b-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="ff96b-123">Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="ff96b-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff96b-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ff96b-124">Return Value</span></span>  
 <span data-ttu-id="ff96b-125">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="ff96b-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff96b-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff96b-126">Requirements</span></span>  
 <span data-ttu-id="ff96b-127">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ff96b-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff96b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff96b-128">See also</span></span>
- [<span data-ttu-id="ff96b-129">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="ff96b-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="ff96b-130">DefineGlobalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="ff96b-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="ff96b-131">DefineLocalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="ff96b-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
