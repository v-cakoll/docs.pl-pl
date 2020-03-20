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
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178438"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="e7e45-102">ICoreClrDebugTarget::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="e7e45-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="e7e45-103">Wylicza procesy, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="e7e45-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7e45-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7e45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7e45-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="e7e45-106">[na zewnątrz] Liczba procesów zwróconych w `ppProcs`pliku .</span><span class="sxs-lookup"><span data-stu-id="e7e45-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="e7e45-107">Ta wartość może wynosić 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="e7e45-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="e7e45-108">[na zewnątrz] Tablica [struktur CoreClrDebugProcInfo,](coreclrdebugprocinfo-structure.md) które reprezentują procesy uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="e7e45-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7e45-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e7e45-109">Return Value</span></span>  
 <span data-ttu-id="e7e45-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7e45-110">S_OK</span></span>  
 <span data-ttu-id="e7e45-111">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="e7e45-111">Success.</span></span>  
  
 <span data-ttu-id="e7e45-112">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="e7e45-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="e7e45-113">Nie można przydzielić `ppProcs`wystarczającej ilości pamięci dla pliku .</span><span class="sxs-lookup"><span data-stu-id="e7e45-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="e7e45-114">E_FAIL (lub inne E_ kody zwrotne)</span><span class="sxs-lookup"><span data-stu-id="e7e45-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e7e45-115">Inne awarie.</span><span class="sxs-lookup"><span data-stu-id="e7e45-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7e45-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7e45-116">Remarks</span></span>  
 <span data-ttu-id="e7e45-117">Aby zwolnić pamięć, która została przydzielona przez tę metodę, wywołaj [metodę ICoreClrDebugTarget::FreeMemory.](icoreclrdebugtarget-freememory-method.md)</span><span class="sxs-lookup"><span data-stu-id="e7e45-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7e45-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7e45-118">Requirements</span></span>  
 <span data-ttu-id="e7e45-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7e45-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7e45-120">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e7e45-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e7e45-121">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e7e45-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e7e45-122">**Wersje .NET Framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e7e45-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e45-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7e45-123">See also</span></span>

- [<span data-ttu-id="e7e45-124">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7e45-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
