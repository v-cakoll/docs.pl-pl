---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineLocalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1124b57bed16e349c753be872c1b709a287e6237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="6ec77-102">ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ec77-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="6ec77-103">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalne.</span><span class="sxs-lookup"><span data-stu-id="6ec77-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="6ec77-104">Tę metodę można wywoływać wielokrotnie dla zmiennej o tej samej nazwie, który ma wiele domach w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6ec77-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="6ec77-105">W tym przypadku jednak wartości `startOffset` i `endOffset` parametrów nie może nakładać się na.</span><span class="sxs-lookup"><span data-stu-id="6ec77-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec77-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ec77-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="6ec77-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ec77-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6ec77-108">[in] Nazwa zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6ec77-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="6ec77-109">[in] Atrybuty zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="6ec77-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="6ec77-110">[in] Token metadanych podpisu.</span><span class="sxs-lookup"><span data-stu-id="6ec77-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="6ec77-111">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="6ec77-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="6ec77-112">[in] Pierwszy adres Specyfikacja parametru.</span><span class="sxs-lookup"><span data-stu-id="6ec77-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="6ec77-113">[in] Drugi adres Specyfikacja parametru.</span><span class="sxs-lookup"><span data-stu-id="6ec77-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="6ec77-114">[in] Trzeci adres Specyfikacja parametru.</span><span class="sxs-lookup"><span data-stu-id="6ec77-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="6ec77-115">[in] Przesunięcie początku zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6ec77-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="6ec77-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6ec77-116">This parameter is optional.</span></span> <span data-ttu-id="6ec77-117">Jeśli jest 0, ten parametr jest ignorowany i zmienna jest zdefiniowana w całym całego zakresu.</span><span class="sxs-lookup"><span data-stu-id="6ec77-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="6ec77-118">Jeśli wartość niezerową, zmiennej spełnia przesunięcia bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="6ec77-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="6ec77-119">[in] Przesunięcie zakończenia dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6ec77-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="6ec77-120">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6ec77-120">This parameter is optional.</span></span> <span data-ttu-id="6ec77-121">Jeśli jest 0, ten parametr jest ignorowany i zmienna jest zdefiniowana w całym całego zakresu.</span><span class="sxs-lookup"><span data-stu-id="6ec77-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="6ec77-122">Jeśli wartość niezerową, zmiennej spełnia przesunięcia bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="6ec77-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ec77-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ec77-123">Return Value</span></span>  
 <span data-ttu-id="6ec77-124">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6ec77-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec77-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ec77-125">Requirements</span></span>  
 <span data-ttu-id="6ec77-126">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="6ec77-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec77-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ec77-127">See Also</span></span>  
 [<span data-ttu-id="6ec77-128">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ec77-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="6ec77-129">DefineLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="6ec77-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
