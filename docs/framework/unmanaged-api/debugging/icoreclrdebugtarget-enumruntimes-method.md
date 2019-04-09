---
title: ICoreClrDebugTarget::EnumRuntimes — Metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afb31646d21ec7e15f79601f5fe83ea6ce44fa90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134683"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="e3da8-102">ICoreClrDebugTarget::EnumRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3da8-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="e3da8-103">Wylicza środowiska uruchomieniowego języka wspólnego (CLRs) w określonym procesie, który jest uruchomiona na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="e3da8-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3da8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3da8-104">Syntax</span></span>  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3da8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3da8-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="e3da8-106">[in] Wewnętrzny proces identyfikator procesu, dla którego chcesz wyliczyć środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="e3da8-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="e3da8-107">Będzie to `m_dwInternalID` od odpowiadających im [coreclrdebugprocinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="e3da8-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="e3da8-108">[out] Liczba środowisk uruchomieniowych zwracane w `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="e3da8-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="e3da8-109">Ta wartość może być 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="e3da8-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="e3da8-110">[out] Tablica [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktur, które reprezentują środowiska uruchomieniowego załadowany w procesie docelowym zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e3da8-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3da8-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3da8-111">Return Value</span></span>  
 <span data-ttu-id="e3da8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3da8-112">S_OK</span></span>  
 <span data-ttu-id="e3da8-113">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="e3da8-113">Success.</span></span>  
  
 <span data-ttu-id="e3da8-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e3da8-114">S_FALSE</span></span>  
 `dwInternalProcessID` <span data-ttu-id="e3da8-115">nie pasuje żaden proces, który jest uruchomiony na komputerze, prawdopodobnie ponieważ proces został zakończony.</span><span class="sxs-lookup"><span data-stu-id="e3da8-115">does not match any process that is running on the computer, probably because the process was terminated.</span></span> `pcRuntimes` <span data-ttu-id="e3da8-116">i `ppRuntimes` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="e3da8-116">and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="e3da8-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e3da8-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="e3da8-118">Nie można przydzielić wystarczającej ilości pamięci do `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="e3da8-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="e3da8-119">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="e3da8-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e3da8-120">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="e3da8-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3da8-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3da8-121">Remarks</span></span>  
 <span data-ttu-id="e3da8-122">Aby zwolnić pamięć, która została przydzielona przez tę metodę, należy wywołać [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e3da8-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3da8-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3da8-123">Requirements</span></span>  
 <span data-ttu-id="e3da8-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3da8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3da8-125">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e3da8-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e3da8-126">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e3da8-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e3da8-127">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="e3da8-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3da8-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3da8-128">See also</span></span>

- [<span data-ttu-id="e3da8-129">ICoreClrDebugTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e3da8-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
