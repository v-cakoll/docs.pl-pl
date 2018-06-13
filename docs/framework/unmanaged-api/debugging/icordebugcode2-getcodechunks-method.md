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
ms.openlocfilehash: bdfcd45b15ddc1491b12de0fa42901b6d3f7fe9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413156"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="1ef58-102">ICorDebugCode2::GetCodeChunks — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ef58-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="1ef58-103">Pobiera fragmentów kodu, który składa się ten obiekt kodu z.</span><span class="sxs-lookup"><span data-stu-id="1ef58-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ef58-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ef58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ef58-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="1ef58-106">[in] Rozmiar `chunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1ef58-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="1ef58-107">[out] Liczba fragmentów zwracane w `chunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1ef58-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="1ef58-108">[out] Tablica struktury "CodeChunkInfo", z których każdy reprezentuje jednego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="1ef58-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="1ef58-109">Jeśli wartość `cbufSize` wynosi 0, ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="1ef58-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef58-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ef58-110">Remarks</span></span>  
 <span data-ttu-id="1ef58-111">Fragmenty kodu nigdy nie będzie nakłada, a użytkownicy zastosują kolejność, w którym one będzie mieć został połączony przez [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="1ef58-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="1ef58-112">Obiekt kodu języka pośredniego (MSIL) firmy Microsoft, w programie .NET Framework w wersji 2.0 obejmuje fragmentu kodu pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="1ef58-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef58-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ef58-113">Requirements</span></span>  
 <span data-ttu-id="1ef58-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef58-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef58-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ef58-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ef58-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ef58-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ef58-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef58-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef58-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ef58-118">See Also</span></span>  
 
