---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e0493ed3f8796019d5715ef468c88675b9970a39
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973700"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="da053-102">ICorProfilerInfo9:: GetCodeInfo4, Metoda</span><span class="sxs-lookup"><span data-stu-id="da053-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>
  
 <span data-ttu-id="da053-103">Przy podanym adresie początkowym kodu natywnego program zwraca bloki pamięci wirtualnej, która przechowuje ten kod.</span><span class="sxs-lookup"><span data-stu-id="da053-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="da053-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da053-104">Syntax</span></span>  
  
```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="da053-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da053-105">Parameters</span></span>  
 `pNativeCodeStartAddress`  
 <span data-ttu-id="da053-106">podczas Wskaźnik do początku funkcji natywnej.</span><span class="sxs-lookup"><span data-stu-id="da053-106">[in] A pointer to the start of a native function.</span></span>  

 `cCodeInfos`  
 <span data-ttu-id="da053-107">podczas Rozmiar `codeInfos` tablicy.</span><span class="sxs-lookup"><span data-stu-id="da053-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="da053-108">określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="da053-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="da053-109">określoną Bufor dostarczony przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="da053-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="da053-110">Po powrocie metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy opisuje blok kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="da053-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da053-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da053-111">Remarks</span></span>  
 <span data-ttu-id="da053-112">Metoda jest podobna do GetCodeInfo3 —, z tą różnicą, że może wyszukiwać informacje o kodzie dla różnych natywnych wersji metody. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md) `GetCodeInfo4`</span><span class="sxs-lookup"><span data-stu-id="da053-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da053-113">`GetCodeInfo4`może wyzwolić wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="da053-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>
  
 <span data-ttu-id="da053-114">Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="da053-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="da053-115">Po `GetCodeInfo4` powrocie należy sprawdzić `codeInfos` , czy bufor jest wystarczająco duży, aby można było zawierać wszystkie struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="da053-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="da053-116">W tym celu należy porównać wartość `cCodeInfos` z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="da053-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="da053-117">Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) jest `pcCodeInfos`mniejsza niż, Przydziel większy `codeInfos` bufor, zaktualizuj `cCodeInfos` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetCodeInfo4` .</span><span class="sxs-lookup"><span data-stu-id="da053-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>  
  
 <span data-ttu-id="da053-118">Alternatywnie, można najpierw wywołać `GetCodeInfo4` z buforem o zerowej długości `codeInfos` , aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="da053-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="da053-119">Następnie `codeInfos` można ustawić rozmiar buforu na wartość zwróconą `pcCodeInfos`w, pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) i ponownie wywołać `GetCodeInfo4` .</span><span class="sxs-lookup"><span data-stu-id="da053-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>   
  

## <a name="requirements"></a><span data-ttu-id="da053-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da053-120">Requirements</span></span>  
 <span data-ttu-id="da053-121">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="da053-121">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="da053-122">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="da053-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da053-123">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da053-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da053-124">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da053-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="da053-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da053-125">See also</span></span>
- [<span data-ttu-id="da053-126">ICorProfilerInfo9, interfejs</span><span class="sxs-lookup"><span data-stu-id="da053-126">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)

