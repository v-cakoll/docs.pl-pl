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
ms.openlocfilehash: 73f536b4ab98aa596c2395810cb8b616ffd309e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438293"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="f04cc-102">ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="f04cc-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="f04cc-103">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="f04cc-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="f04cc-104">Tę metodę można wywołać wiele razy dla zmiennej o tej samej nazwie, która ma wiele domów w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f04cc-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="f04cc-105">Jednak w takim przypadku wartości `startOffset` i `endOffset` parametrów nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="f04cc-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f04cc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f04cc-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="f04cc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f04cc-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f04cc-108">podczas Nazwa zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f04cc-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="f04cc-109">podczas Atrybuty zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f04cc-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="f04cc-110">podczas Token metadanych sygnatury.</span><span class="sxs-lookup"><span data-stu-id="f04cc-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="f04cc-111">podczas Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="f04cc-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="f04cc-112">podczas Pierwszy adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="f04cc-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="f04cc-113">podczas Drugi adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="f04cc-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="f04cc-114">podczas Trzeci adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="f04cc-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="f04cc-115">podczas Przesunięcie początkowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f04cc-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="f04cc-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f04cc-116">This parameter is optional.</span></span> <span data-ttu-id="f04cc-117">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f04cc-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="f04cc-118">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="f04cc-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="f04cc-119">podczas Przesunięcie końcowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f04cc-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="f04cc-120">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f04cc-120">This parameter is optional.</span></span> <span data-ttu-id="f04cc-121">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f04cc-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="f04cc-122">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="f04cc-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f04cc-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f04cc-123">Return Value</span></span>  
 <span data-ttu-id="f04cc-124">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f04cc-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f04cc-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f04cc-125">Requirements</span></span>  
 <span data-ttu-id="f04cc-126">**Nagłówek:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="f04cc-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f04cc-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f04cc-127">See also</span></span>

- [<span data-ttu-id="f04cc-128">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f04cc-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="f04cc-129">DefineLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="f04cc-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
