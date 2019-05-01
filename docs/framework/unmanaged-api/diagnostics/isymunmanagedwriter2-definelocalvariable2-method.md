---
title: ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2caa9b48fc92a1b2e82f574d37d99758e19382c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777972"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="5239a-102">ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="5239a-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="5239a-103">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="5239a-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="5239a-104">Tę metodę można wywoływać wielokrotnie dla zmiennej o tej samej nazwie, który ma wiele domów w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5239a-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="5239a-105">W takim jednak wartości `startOffset` i `endOffset` parametry nie mogą się nakładać.</span><span class="sxs-lookup"><span data-stu-id="5239a-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5239a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5239a-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5239a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5239a-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5239a-108">[in] Lokalna nazwa zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5239a-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="5239a-109">[in] Lokalne atrybuty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5239a-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="5239a-110">[in] Token metadanych podpisu.</span><span class="sxs-lookup"><span data-stu-id="5239a-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="5239a-111">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="5239a-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="5239a-112">[in] Pierwszy adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="5239a-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="5239a-113">[in] Drugi adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="5239a-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="5239a-114">[in] Trzeci adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="5239a-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="5239a-115">[in] Przesunięcie początku dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5239a-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="5239a-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5239a-116">This parameter is optional.</span></span> <span data-ttu-id="5239a-117">Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres.</span><span class="sxs-lookup"><span data-stu-id="5239a-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="5239a-118">Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="5239a-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="5239a-119">[in] Przesunięcie zakończenia dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5239a-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="5239a-120">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5239a-120">This parameter is optional.</span></span> <span data-ttu-id="5239a-121">Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres.</span><span class="sxs-lookup"><span data-stu-id="5239a-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="5239a-122">Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="5239a-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5239a-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5239a-123">Return Value</span></span>  
 <span data-ttu-id="5239a-124">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="5239a-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5239a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5239a-125">Requirements</span></span>  
 <span data-ttu-id="5239a-126">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="5239a-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5239a-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5239a-127">See also</span></span>

- [<span data-ttu-id="5239a-128">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5239a-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="5239a-129">DefineLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="5239a-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
