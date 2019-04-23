---
title: ICoreClrDebugTarget::EnumProcesses — Metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a35f5ff62ca37337b7becb023f2328cbe05aea6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216044"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="5ffa1-102">ICoreClrDebugTarget::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="5ffa1-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="5ffa1-103">Wylicza procesów, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="5ffa1-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffa1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ffa1-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ffa1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ffa1-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="5ffa1-106">[out] Liczba procesów zwracane w `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="5ffa1-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="5ffa1-107">Ta wartość może być 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="5ffa1-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="5ffa1-108">[out] Tablica [coreclrdebugprocinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) struktur, które reprezentują procesy uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="5ffa1-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ffa1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5ffa1-109">Return Value</span></span>  
 <span data-ttu-id="5ffa1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ffa1-110">S_OK</span></span>  
 <span data-ttu-id="5ffa1-111">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="5ffa1-111">Success.</span></span>  
  
 <span data-ttu-id="5ffa1-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5ffa1-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="5ffa1-113">Nie można przydzielić wystarczającej ilości pamięci do `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="5ffa1-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="5ffa1-114">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="5ffa1-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5ffa1-115">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="5ffa1-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ffa1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ffa1-116">Remarks</span></span>  
 <span data-ttu-id="5ffa1-117">Aby zwolnić pamięć, która została przydzielona przez tę metodę, należy wywołać [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5ffa1-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ffa1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ffa1-118">Requirements</span></span>  
 <span data-ttu-id="5ffa1-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ffa1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffa1-120">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="5ffa1-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="5ffa1-121">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="5ffa1-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="5ffa1-122">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="5ffa1-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffa1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ffa1-123">See also</span></span>

- [<span data-ttu-id="5ffa1-124">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ffa1-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
