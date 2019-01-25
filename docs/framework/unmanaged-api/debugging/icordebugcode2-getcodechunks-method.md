---
title: ICorDebugCode2::GetCodeChunks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf8bc747f643819eb82448b4ad6b7fab696c9c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572503"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="1aa5b-102">ICorDebugCode2::GetCodeChunks — Metoda</span><span class="sxs-lookup"><span data-stu-id="1aa5b-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="1aa5b-103">Pobiera fragmentów kodu, który składa się ten obiekt kodu z.</span><span class="sxs-lookup"><span data-stu-id="1aa5b-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1aa5b-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1aa5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1aa5b-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="1aa5b-106">[in] Rozmiar `chunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1aa5b-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="1aa5b-107">[out] Liczba fragmentów zwracane w `chunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1aa5b-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="1aa5b-108">[out] Tablica struktur "codechunkinfo —", z których każdy reprezentuje jeden fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="1aa5b-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="1aa5b-109">Jeśli wartość `cbufSize` wynosi 0, ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="1aa5b-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aa5b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1aa5b-110">Remarks</span></span>  
 <span data-ttu-id="1aa5b-111">Fragmenty kodu będzie nigdy nie nakładają się na siebie, a zostanie postępuj zgodnie z kolejności, w którym ich będzie mieć zostały połączone przez [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="1aa5b-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="1aa5b-112">Obiekt kodu języka intermediate language (MSIL) firmy Microsoft, w .NET Framework w wersji 2.0 będzie zawierać fragmentów pojedynczego kodu.</span><span class="sxs-lookup"><span data-stu-id="1aa5b-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aa5b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1aa5b-113">Requirements</span></span>  
 <span data-ttu-id="1aa5b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aa5b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aa5b-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aa5b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aa5b-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aa5b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aa5b-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa5b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa5b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1aa5b-118">See also</span></span>

