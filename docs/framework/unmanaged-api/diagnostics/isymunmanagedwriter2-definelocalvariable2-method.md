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
ms.openlocfilehash: ac7559bd5431f45b266602404ddde9081aa2944d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614698"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="d32d2-102">ISymUnmanagedWriter2::DefineLocalVariable2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="d32d2-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="d32d2-103">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="d32d2-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="d32d2-104">Tę metodę można wywołać wiele razy dla zmiennej o tej samej nazwie, która ma wiele domów w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d32d2-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="d32d2-105">Jednak w takim przypadku wartości `startOffset` `endOffset` parametrów i nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="d32d2-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d32d2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d32d2-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d32d2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d32d2-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d32d2-108">podczas Nazwa zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d32d2-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="d32d2-109">podczas Atrybuty zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d32d2-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="d32d2-110">podczas Token metadanych sygnatury.</span><span class="sxs-lookup"><span data-stu-id="d32d2-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="d32d2-111">podczas Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="d32d2-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="d32d2-112">podczas Pierwszy adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="d32d2-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="d32d2-113">podczas Drugi adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="d32d2-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="d32d2-114">podczas Trzeci adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="d32d2-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="d32d2-115">podczas Przesunięcie początkowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d32d2-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="d32d2-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d32d2-116">This parameter is optional.</span></span> <span data-ttu-id="d32d2-117">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d32d2-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="d32d2-118">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="d32d2-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="d32d2-119">podczas Przesunięcie końcowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d32d2-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="d32d2-120">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d32d2-120">This parameter is optional.</span></span> <span data-ttu-id="d32d2-121">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d32d2-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="d32d2-122">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="d32d2-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d32d2-123">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d32d2-123">Return Value</span></span>  
 <span data-ttu-id="d32d2-124">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d32d2-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d32d2-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d32d2-125">Requirements</span></span>  
 <span data-ttu-id="d32d2-126">**Nagłówek:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="d32d2-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d32d2-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d32d2-127">See also</span></span>

- [<span data-ttu-id="d32d2-128">ISymUnmanagedWriter2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d32d2-128">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="d32d2-129">DefineLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="d32d2-129">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
