---
title: ICorDebugCode::GetCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178997"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="6c4f3-102">ICorDebugCode::GetCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c4f3-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="6c4f3-103">Pobiera cały kod dla określonej funkcji, sformatowany do demontażu.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="6c4f3-104">Ta metoda została przestarzała w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6c4f3-105">Zamiast tego użyj [funkcji ICorDebugCode2::GetCodeChunks.](icordebugcode2-getcodechunks-method.md)</span><span class="sxs-lookup"><span data-stu-id="6c4f3-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4f3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c4f3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c4f3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c4f3-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="6c4f3-108">[w] Przesunięcie początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="6c4f3-109">[w] Przesunięcie końca funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="6c4f3-110">[w] Rozmiar tablicy, `buffer` do której zostanie zwrócony kod.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="6c4f3-111">[na zewnątrz] Tablica, do której zostanie zwrócony kod.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="6c4f3-112">[na zewnątrz] Liczba zwracanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c4f3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c4f3-113">Remarks</span></span>  
 <span data-ttu-id="6c4f3-114">Jeśli kod funkcji został podzielony na wiele fragmentów, są one łączone w kolejności zwiększania natywnego odsunięcia.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="6c4f3-115">Granice instrukcji nie są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="6c4f3-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c4f3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c4f3-116">Requirements</span></span>  
 <span data-ttu-id="6c4f3-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c4f3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c4f3-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c4f3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c4f3-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c4f3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c4f3-120">**Wersje programu .NET Framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="6c4f3-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4f3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c4f3-121">See also</span></span>

- [<span data-ttu-id="6c4f3-122">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="6c4f3-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
