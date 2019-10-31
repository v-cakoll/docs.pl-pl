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
ms.openlocfilehash: 2579bed9ae432a2b9460c421c6ee5bdc40d1e149
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121838"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="0c696-102">ICoreClrDebugTarget::EnumRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c696-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="0c696-103">Wylicza środowisko uruchomieniowe języka wspólnego (CLRs) w określonym procesie, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="0c696-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c696-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c696-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c696-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c696-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="0c696-106">podczas Wewnętrzny identyfikator procesu, dla którego mają zostać wyliczone środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0c696-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="0c696-107">Zostanie `m_dwInternalID` od odpowiedniego [CoreClrDebugProcInfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="0c696-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="0c696-108">określoną Liczba środowisk uruchomieniowych zwróconych w `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="0c696-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="0c696-109">Ta wartość może być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="0c696-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="0c696-110">określoną Tablica struktur [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) , które reprezentują środowiska uruchomieniowe ładowane w zdalnym procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="0c696-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c696-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0c696-111">Return Value</span></span>  
 <span data-ttu-id="0c696-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c696-112">S_OK</span></span>  
 <span data-ttu-id="0c696-113">Prawnego.</span><span class="sxs-lookup"><span data-stu-id="0c696-113">Success.</span></span>  
  
 <span data-ttu-id="0c696-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0c696-114">S_FALSE</span></span>  
 <span data-ttu-id="0c696-115">`dwInternalProcessID` nie pasuje do żadnego procesu uruchomionego na komputerze, prawdopodobnie dlatego, że proces został zakończony.</span><span class="sxs-lookup"><span data-stu-id="0c696-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="0c696-116">`pcRuntimes` i `ppRuntimes` będą mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="0c696-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="0c696-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0c696-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="0c696-118">Nie można przydzielić wystarczającej ilości pamięci dla `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="0c696-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="0c696-119">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="0c696-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0c696-120">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="0c696-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c696-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c696-121">Remarks</span></span>  
 <span data-ttu-id="0c696-122">Aby zwolnić pamięć, która została przypisana przez tę metodę, wywołaj metodę [ICoreClrDebugTarget:: freememory —](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0c696-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c696-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c696-123">Requirements</span></span>  
 <span data-ttu-id="0c696-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c696-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c696-125">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="0c696-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0c696-126">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="0c696-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0c696-127">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="0c696-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c696-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c696-128">See also</span></span>

- [<span data-ttu-id="0c696-129">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c696-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
