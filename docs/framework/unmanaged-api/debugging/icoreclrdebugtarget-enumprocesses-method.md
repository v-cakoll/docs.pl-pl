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
ms.openlocfilehash: 11b1072b3467f7d0a3f223fbc2151ec9ccf461ad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790801"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="d9f9a-102">ICoreClrDebugTarget::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9f9a-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="d9f9a-103">Wylicza procesy, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="d9f9a-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9f9a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9f9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9f9a-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="d9f9a-106">określoną Liczba procesów zwróconych w `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="d9f9a-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="d9f9a-107">Ta wartość może być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="d9f9a-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="d9f9a-108">określoną Tablica struktur [CoreClrDebugProcInfo —](coreclrdebugprocinfo-structure.md) , które reprezentują procesy uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="d9f9a-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9f9a-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="d9f9a-109">Return Value</span></span>  
 <span data-ttu-id="d9f9a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9f9a-110">S_OK</span></span>  
 <span data-ttu-id="d9f9a-111">Prawnego.</span><span class="sxs-lookup"><span data-stu-id="d9f9a-111">Success.</span></span>  
  
 <span data-ttu-id="d9f9a-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d9f9a-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="d9f9a-113">Nie można przydzielić wystarczającej ilości pamięci dla `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="d9f9a-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="d9f9a-114">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="d9f9a-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d9f9a-115">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="d9f9a-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9f9a-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9f9a-116">Remarks</span></span>  
 <span data-ttu-id="d9f9a-117">Aby zwolnić pamięć, która została przypisana przez tę metodę, wywołaj metodę [ICoreClrDebugTarget:: freememory —](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9f9a-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9f9a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9f9a-118">Requirements</span></span>  
 <span data-ttu-id="d9f9a-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9f9a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9f9a-120">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="d9f9a-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d9f9a-121">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="d9f9a-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d9f9a-122">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d9f9a-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f9a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9f9a-123">See also</span></span>

- [<span data-ttu-id="d9f9a-124">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9f9a-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
