---
title: CoEEShutDownCOM — Funkcja
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 164384f043a1722ace6e5c4098cb31c4327cba1e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044060"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="70a1c-102">CoEEShutDownCOM — Funkcja</span><span class="sxs-lookup"><span data-stu-id="70a1c-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="70a1c-103">Wymusza, aby środowisko uruchomieniowe języka wspólnego (CLR) zwolnił wszystkie wskaźniki interfejsu, które znajdują się wewnątrz wywoływanych otok (RCW) środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="70a1c-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="70a1c-104">Ma to wpływ na zwalnianie wszystkich pamięci podręcznych OTOKi.</span><span class="sxs-lookup"><span data-stu-id="70a1c-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="70a1c-105">Ta funkcja globalna jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="70a1c-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="70a1c-106">Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="70a1c-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a1c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="70a1c-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="70a1c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70a1c-108">Remarks</span></span>  
 <span data-ttu-id="70a1c-109">`CoEEShutDownCOM` Funkcja najpierw zwalnia wszystkie RCW we wszystkich kontekstach i we wszystkich pamięciach podręcznych, a następnie usuwa wszelkie powiadomienia o rozrywaniu istniejące w instalatorze.</span><span class="sxs-lookup"><span data-stu-id="70a1c-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="70a1c-110">Brak wyładowywania biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="70a1c-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="70a1c-111">Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="70a1c-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="70a1c-112">Począwszy od .NET Framework 4, wywołaj punkt wejścia dla tej funkcji w konkretnym środowisku uruchomieniowym, którego chcesz dotyczyć.</span><span class="sxs-lookup"><span data-stu-id="70a1c-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="70a1c-113">Aby uzyskać punkt wejścia, wywołaj metodę [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) i określ wartość "CoEEShutDownCOM —".</span><span class="sxs-lookup"><span data-stu-id="70a1c-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70a1c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70a1c-114">Requirements</span></span>  
 <span data-ttu-id="70a1c-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70a1c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a1c-116">**Nagłówki** Cor. h</span><span class="sxs-lookup"><span data-stu-id="70a1c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70a1c-117">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="70a1c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70a1c-118">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70a1c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a1c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70a1c-119">See also</span></span>

- [<span data-ttu-id="70a1c-120">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="70a1c-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
