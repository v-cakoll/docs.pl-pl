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
ms.openlocfilehash: 14b5f2227991e38ba66889d7e966ab24e714294c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="a3dfc-102">ICoreClrDebugTarget::EnumRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3dfc-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="a3dfc-103">Wylicza wspólnej obsługi language (CLRs) określonego procesu uruchomionego na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3dfc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3dfc-104">Syntax</span></span>  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3dfc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3dfc-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="a3dfc-106">[in] Wewnętrzny proces identyfikator procesu, który ma wyliczyć środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="a3dfc-107">Są to `m_dwInternalID` z odpowiadającego [coreclrdebugprocinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="a3dfc-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="a3dfc-108">[out] Liczba zwracanych w środowiskach uruchomieniowych `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="a3dfc-109">Ta wartość może być 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="a3dfc-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="a3dfc-110">[out] Tablica [coreclrdebugruntimeinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktur reprezentujących środowisk uruchomieniowych załadowany w procesie docelowym zdalnego.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3dfc-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3dfc-111">Return Value</span></span>  
 <span data-ttu-id="a3dfc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3dfc-112">S_OK</span></span>  
 <span data-ttu-id="a3dfc-113">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-113">Success.</span></span>  
  
 <span data-ttu-id="a3dfc-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a3dfc-114">S_FALSE</span></span>  
 <span data-ttu-id="a3dfc-115">`dwInternalProcessID` nie odpowiada żaden proces, który jest uruchomiony na komputerze, prawdopodobnie, ponieważ proces został zakończony.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="a3dfc-116">`pcRuntimes` i `ppRuntimes` będzie mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="a3dfc-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a3dfc-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a3dfc-118">Nie można przydzielić wystarczającej ilości pamięci do `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="a3dfc-119">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="a3dfc-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a3dfc-120">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3dfc-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3dfc-121">Remarks</span></span>  
 <span data-ttu-id="a3dfc-122">Aby zwolnić pamięć, która została przydzielona przez tę metodę, należy wywołać [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a3dfc-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3dfc-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3dfc-123">Requirements</span></span>  
 <span data-ttu-id="a3dfc-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3dfc-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3dfc-125">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="a3dfc-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a3dfc-126">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a3dfc-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a3dfc-127">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="a3dfc-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3dfc-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3dfc-128">See Also</span></span>  
 [<span data-ttu-id="a3dfc-129">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3dfc-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
