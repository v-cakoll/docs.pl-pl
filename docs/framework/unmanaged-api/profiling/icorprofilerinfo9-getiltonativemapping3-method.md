---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 46ceef43806fda9956797935c5eeec61f865dc6e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973685"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="ad31b-102">ICorProfilerInfo9:: GetILToNativeMapping3, Metoda</span><span class="sxs-lookup"><span data-stu-id="ad31b-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>
  
 <span data-ttu-id="ad31b-103">Przy podanym adresie początkowym kodu natywnego program zwraca informacje mapowania natywnego do IL dla tej trybie JIT wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="ad31b-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="ad31b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad31b-104">Syntax</span></span>  
  
```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad31b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad31b-105">Parameters</span></span>  
 `pNativeCodeStartAddress` \
 <span data-ttu-id="ad31b-106">podczas Wskaźnik do początku funkcji natywnej.</span><span class="sxs-lookup"><span data-stu-id="ad31b-106">[in] A pointer to the start of a native function.</span></span>

 `cMap` \
 <span data-ttu-id="ad31b-107">podczas Maksymalny rozmiar `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad31b-107">[in] The maximum size of the `map` array.</span></span> 

 `pcMap` \
 <span data-ttu-id="ad31b-108">określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.</span><span class="sxs-lookup"><span data-stu-id="ad31b-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

 `map` \
 <span data-ttu-id="ad31b-109">określoną Tablica struktur [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , z których każdy określa przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="ad31b-109">[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="ad31b-110">Po powrocie `GetILToNativeMapping3` metody `COR_DEBUG_IL_TO_NATIVE_MAP` będzie zawierać niektóre `map` lub wszystkie struktury.</span><span class="sxs-lookup"><span data-stu-id="ad31b-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad31b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad31b-111">Remarks</span></span>  
 <span data-ttu-id="ad31b-112">Gdy kompilacja warstwowa jest włączona, Metoda może mieć więcej niż jedną treść kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="ad31b-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="ad31b-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) zwróci adresy startowe dla wszystkich natywnych treści kodu.</span><span class="sxs-lookup"><span data-stu-id="ad31b-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad31b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad31b-114">Requirements</span></span>  
 <span data-ttu-id="ad31b-115">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="ad31b-115">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="ad31b-116">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ad31b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad31b-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad31b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad31b-118">**.NET Framework wersje:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad31b-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="ad31b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad31b-119">See also</span></span>
- [<span data-ttu-id="ad31b-120">ICorProfilerInfo9, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad31b-120">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

