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
ms.openlocfilehash: 4b55ac1d895bfecbe74be447bd06f4aa22b9d04f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790793"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="377e1-102">ICoreClrDebugTarget::EnumRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="377e1-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="377e1-103">Wylicza środowisko uruchomieniowe języka wspólnego (CLRs) w określonym procesie, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="377e1-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="377e1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="377e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="377e1-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="377e1-106">podczas Wewnętrzny identyfikator procesu, dla którego mają zostać wyliczone środowiska uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="377e1-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="377e1-107">Zostanie `m_dwInternalID` od odpowiedniego [CoreClrDebugProcInfo —](coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="377e1-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="377e1-108">określoną Liczba środowisk uruchomieniowych zwróconych w `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="377e1-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="377e1-109">Ta wartość może być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="377e1-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="377e1-110">określoną Tablica struktur [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) , które reprezentują środowiska uruchomieniowe ładowane w zdalnym procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="377e1-110">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="377e1-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="377e1-111">Return Value</span></span>  
 <span data-ttu-id="377e1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="377e1-112">S_OK</span></span>  
 <span data-ttu-id="377e1-113">Prawnego.</span><span class="sxs-lookup"><span data-stu-id="377e1-113">Success.</span></span>  
  
 <span data-ttu-id="377e1-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="377e1-114">S_FALSE</span></span>  
 <span data-ttu-id="377e1-115">`dwInternalProcessID` nie pasuje do żadnego procesu uruchomionego na komputerze, prawdopodobnie dlatego, że proces został zakończony.</span><span class="sxs-lookup"><span data-stu-id="377e1-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="377e1-116">`pcRuntimes` i `ppRuntimes` będą mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="377e1-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="377e1-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="377e1-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="377e1-118">Nie można przydzielić wystarczającej ilości pamięci dla `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="377e1-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="377e1-119">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="377e1-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="377e1-120">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="377e1-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="377e1-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="377e1-121">Remarks</span></span>  
 <span data-ttu-id="377e1-122">Aby zwolnić pamięć, która została przypisana przez tę metodę, wywołaj metodę [ICoreClrDebugTarget:: freememory —](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="377e1-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="377e1-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="377e1-123">Requirements</span></span>  
 <span data-ttu-id="377e1-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="377e1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="377e1-125">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="377e1-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="377e1-126">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="377e1-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="377e1-127">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="377e1-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377e1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="377e1-128">See also</span></span>

- [<span data-ttu-id="377e1-129">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="377e1-129">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
