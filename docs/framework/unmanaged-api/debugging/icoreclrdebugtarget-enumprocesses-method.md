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
ms.openlocfilehash: c09b70b5afb0561d32e55dd89df6cac083abc068
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="4af42-102">ICoreClrDebugTarget::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="4af42-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="4af42-103">Wylicza procesów, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="4af42-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4af42-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4af42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4af42-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="4af42-106">[out] Liczba procesów zwracane w `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="4af42-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="4af42-107">Ta wartość może być 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="4af42-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="4af42-108">[out] Tablica [coreclrdebugprocinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) struktur reprezentujących procesów uruchomionych na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="4af42-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4af42-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4af42-109">Return Value</span></span>  
 <span data-ttu-id="4af42-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4af42-110">S_OK</span></span>  
 <span data-ttu-id="4af42-111">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="4af42-111">Success.</span></span>  
  
 <span data-ttu-id="4af42-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4af42-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="4af42-113">Nie można przydzielić wystarczającej ilości pamięci do `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="4af42-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="4af42-114">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="4af42-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4af42-115">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="4af42-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4af42-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4af42-116">Remarks</span></span>  
 <span data-ttu-id="4af42-117">Aby zwolnić pamięć, która została przydzielona przez tę metodę, należy wywołać [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4af42-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af42-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4af42-118">Requirements</span></span>  
 <span data-ttu-id="4af42-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af42-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af42-120">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="4af42-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="4af42-121">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="4af42-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="4af42-122">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="4af42-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af42-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4af42-123">See Also</span></span>  
 [<span data-ttu-id="4af42-124">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="4af42-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
