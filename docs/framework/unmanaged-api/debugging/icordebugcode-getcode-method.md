---
title: "ICorDebugCode::GetCode — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12820d0be725c92754640aaa4eebca56bbc33ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="aeb7d-102">ICorDebugCode::GetCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="aeb7d-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="aeb7d-103">Pobiera cały kod dla określonej funkcji, sformatowany dezasemblacji.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="aeb7d-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="aeb7d-105">Użyj [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb7d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aeb7d-106">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aeb7d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aeb7d-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="aeb7d-108">[in] Przesunięcie początku funkcji.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="aeb7d-109">[in] Przesunięcia końca funkcji.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="aeb7d-110">[in] Rozmiar `buffer` tablicy, do której zostanie zwrócony kod.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="aeb7d-111">[out] Tablica, do którego zostanie zwrócony kod.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="aeb7d-112">[out] Liczba bajtów zwrócona.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeb7d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aeb7d-113">Remarks</span></span>  
 <span data-ttu-id="aeb7d-114">Jeśli kod funkcji został podzielony na wiele fragmentów, są one połączone w porządku rosnących przesunięcie natywnego.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="aeb7d-115">Instrukcja granice nie są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="aeb7d-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb7d-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aeb7d-116">Requirements</span></span>  
 <span data-ttu-id="aeb7d-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb7d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb7d-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeb7d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeb7d-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeb7d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeb7d-120">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="aeb7d-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb7d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aeb7d-121">See Also</span></span>  
 [<span data-ttu-id="aeb7d-122">GetCodeChunks — metoda</span><span class="sxs-lookup"><span data-stu-id="aeb7d-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
