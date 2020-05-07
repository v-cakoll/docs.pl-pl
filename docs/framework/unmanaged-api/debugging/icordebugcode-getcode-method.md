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
ms.openlocfilehash: 59a497d203d241bbc6e0f884007d4a401c112073
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893649"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="7258b-102">ICorDebugCode::GetCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="7258b-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="7258b-103">Pobiera cały kod dla określonej funkcji, sformatowany pod kątem demontażu.</span><span class="sxs-lookup"><span data-stu-id="7258b-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="7258b-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="7258b-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7258b-105">Zamiast tego użyj [ICorDebugCode2:: GetCodeChunks —](icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7258b-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7258b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7258b-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7258b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7258b-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="7258b-108">podczas Przesunięcie początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="7258b-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="7258b-109">podczas Przesunięcie końca funkcji.</span><span class="sxs-lookup"><span data-stu-id="7258b-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="7258b-110">podczas Rozmiar `buffer` tablicy, do której zostanie zwrócony kod.</span><span class="sxs-lookup"><span data-stu-id="7258b-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="7258b-111">określoną Tablica, do której zostanie zwrócony kod.</span><span class="sxs-lookup"><span data-stu-id="7258b-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="7258b-112">określoną Liczba zwróconych bajtów.</span><span class="sxs-lookup"><span data-stu-id="7258b-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7258b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7258b-113">Remarks</span></span>  
 <span data-ttu-id="7258b-114">Jeśli kod funkcji został podzielony na wiele fragmentów, są one łączone w kolejności rosnącego przesunięcia natywnego.</span><span class="sxs-lookup"><span data-stu-id="7258b-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="7258b-115">Granice instrukcji nie są zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="7258b-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7258b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7258b-116">Requirements</span></span>  
 <span data-ttu-id="7258b-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7258b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7258b-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7258b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7258b-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7258b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7258b-120">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="7258b-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7258b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7258b-121">See also</span></span>

- [<span data-ttu-id="7258b-122">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="7258b-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
