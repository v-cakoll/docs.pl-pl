---
title: "ICorDebugCode2::GetCodeChunks — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCodeChunks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b90913f05cc2e0a3e98a5890f76a41eb2eafc6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="da063-102">ICorDebugCode2::GetCodeChunks — Metoda</span><span class="sxs-lookup"><span data-stu-id="da063-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="da063-103">Pobiera fragmentów kodu, który składa się ten obiekt kodu z.</span><span class="sxs-lookup"><span data-stu-id="da063-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da063-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da063-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da063-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da063-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="da063-106">[in] Rozmiar `chunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="da063-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="da063-107">[out] Liczba fragmentów zwracane w `chunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="da063-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="da063-108">[out] Tablica struktury "CodeChunkInfo", z których każdy reprezentuje jednego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="da063-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="da063-109">Jeśli wartość `cbufSize` wynosi 0, ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="da063-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da063-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da063-110">Remarks</span></span>  
 <span data-ttu-id="da063-111">Fragmenty kodu nigdy nie będzie nakłada, a użytkownicy zastosują kolejność, w którym one będzie mieć został połączony przez [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="da063-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="da063-112">Obiekt kodu języka pośredniego (MSIL) firmy Microsoft, w programie .NET Framework w wersji 2.0 obejmuje fragmentu kodu pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="da063-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da063-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da063-113">Requirements</span></span>  
 <span data-ttu-id="da063-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da063-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da063-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da063-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da063-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da063-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da063-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da063-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da063-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da063-118">See Also</span></span>  
 
