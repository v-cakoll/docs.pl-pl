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
ms.openlocfilehash: 5730cdd910257d762230f5e54576d5e0a7ac1adb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614828"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="f79e1-102">ISymUnmanagedWriter::DefineLocalVariable — Metoda</span><span class="sxs-lookup"><span data-stu-id="f79e1-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="f79e1-103">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="f79e1-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="f79e1-104">Tę metodę można wywołać wiele razy dla zmiennej o tej samej nazwie, która ma wiele domów w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f79e1-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="f79e1-105">Jednak w takim przypadku wartości `startOffset` `endOffset` parametrów i nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="f79e1-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79e1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f79e1-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f79e1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f79e1-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f79e1-108">podczas Wskaźnik do elementu `WCHAR` , który definiuje nazwę zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f79e1-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="f79e1-109">podczas Atrybuty zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f79e1-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="f79e1-110">podczas `ULONG32`Wskazuje rozmiar bufora (w bajtach) `signature` .</span><span class="sxs-lookup"><span data-stu-id="f79e1-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="f79e1-111">podczas Podpis zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f79e1-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="f79e1-112">podczas Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="f79e1-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="f79e1-113">podczas Pierwszy adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="f79e1-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="f79e1-114">podczas Drugi adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="f79e1-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="f79e1-115">podczas Trzeci adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="f79e1-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="f79e1-116">podczas Przesunięcie początkowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f79e1-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="f79e1-117">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f79e1-117">This parameter is optional.</span></span> <span data-ttu-id="f79e1-118">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f79e1-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="f79e1-119">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="f79e1-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="f79e1-120">podczas Przesunięcie końcowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f79e1-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="f79e1-121">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f79e1-121">This parameter is optional.</span></span> <span data-ttu-id="f79e1-122">Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f79e1-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="f79e1-123">Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="f79e1-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f79e1-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f79e1-124">Return Value</span></span>  
 <span data-ttu-id="f79e1-125">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f79e1-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f79e1-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f79e1-126">Requirements</span></span>  
 <span data-ttu-id="f79e1-127">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f79e1-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79e1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f79e1-128">See also</span></span>

- [<span data-ttu-id="f79e1-129">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f79e1-129">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="f79e1-130">DefineGlobalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="f79e1-130">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="f79e1-131">DefineLocalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="f79e1-131">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)
