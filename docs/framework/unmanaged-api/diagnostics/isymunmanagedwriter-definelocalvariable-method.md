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
ms.openlocfilehash: f6a741df3ea57b5e9b4fa8bc5d304bfedd1d6c15
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428009"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="e0dc5-102">ISymUnmanagedWriter::DefineLocalVariable — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0dc5-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="e0dc5-103">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="e0dc5-104">Tę metodę można wywołać wiele razy dla zmiennej o tej samej nazwie, która ma wiele domów w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="e0dc5-105">Jednak w takim przypadku wartości `startOffset` i `endOffset` parametrów nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0dc5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0dc5-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="e0dc5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0dc5-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e0dc5-108">podczas Wskaźnik do `WCHAR`, który definiuje nazwę zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="e0dc5-109">podczas Atrybuty zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="e0dc5-110">podczas `ULONG32` wskazujący rozmiar buforu `signature` w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="e0dc5-111">podczas Podpis zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="e0dc5-112">podczas Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="e0dc5-113">podczas Pierwszy adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="e0dc5-114">podczas Drugi adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="e0dc5-115">podczas Trzeci adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="e0dc5-116">podczas Przesunięcie początkowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="e0dc5-117">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-117">This parameter is optional.</span></span> <span data-ttu-id="e0dc5-118">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="e0dc5-119">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="e0dc5-120">podczas Przesunięcie końcowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="e0dc5-121">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-121">This parameter is optional.</span></span> <span data-ttu-id="e0dc5-122">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="e0dc5-123">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0dc5-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0dc5-124">Return Value</span></span>  
 <span data-ttu-id="e0dc5-125">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e0dc5-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0dc5-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0dc5-126">Requirements</span></span>  
 <span data-ttu-id="e0dc5-127">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e0dc5-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0dc5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0dc5-128">See also</span></span>

- [<span data-ttu-id="e0dc5-129">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0dc5-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="e0dc5-130">DefineGlobalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="e0dc5-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="e0dc5-131">DefineLocalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="e0dc5-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
