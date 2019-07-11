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
ms.openlocfilehash: 74548df512f68761b006e064a6db968e82b03813
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779122"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="a65a8-102">CoEEShutDownCOM — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a65a8-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="a65a8-103">Wymusza środowisko uruchomieniowe języka wspólnego (CLR), aby zwolnić wszystkie wskaźniki interfejsu, którą przechowuje wewnątrz wywoływanych otok środowiska uruchomieniowego (RCW).</span><span class="sxs-lookup"><span data-stu-id="a65a8-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="a65a8-104">To powoduje zwolnienie wszystkich RCW pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="a65a8-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="a65a8-105">Ta funkcja globalna jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a65a8-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="a65a8-106">Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a65a8-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65a8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a65a8-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a65a8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a65a8-108">Remarks</span></span>  
 <span data-ttu-id="a65a8-109">`CoEEShutDownCOM` Funkcji najpierw zwalnia RCW we wszystkich kontekstach i wszystkich pamięci podręcznych, a następnie usuwa wszelkie powiadomienia zakończenia istniejące w Instalatorze.</span><span class="sxs-lookup"><span data-stu-id="a65a8-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="a65a8-110">Nie zwalnianie biblioteki DLL występuje.</span><span class="sxs-lookup"><span data-stu-id="a65a8-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a65a8-111">Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="a65a8-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="a65a8-112">Począwszy od programu .NET Framework 4, należy wywołać punkt wejścia dla tej funkcji, od określonego środowiska uruchomieniowego, które mają wpływ na.</span><span class="sxs-lookup"><span data-stu-id="a65a8-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="a65a8-113">Aby uzyskać punkt wejścia, należy wywołać [iclrruntimeinfo::GetProcAddress —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodę i określić "coeeshutdowncom —".</span><span class="sxs-lookup"><span data-stu-id="a65a8-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a65a8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a65a8-114">Requirements</span></span>  
 <span data-ttu-id="a65a8-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a65a8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a65a8-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a65a8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a65a8-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a65a8-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a65a8-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a65a8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65a8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a65a8-119">See also</span></span>

- [<span data-ttu-id="a65a8-120">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="a65a8-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
