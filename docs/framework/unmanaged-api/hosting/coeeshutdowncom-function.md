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
ms.openlocfilehash: d990d63a007240ab0bd0240f7b45fed52e2a2129
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212251"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="a335f-102">CoEEShutDownCOM — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a335f-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="a335f-103">Wymusza środowisko uruchomieniowe języka wspólnego (CLR), aby zwolnić wszystkie wskaźniki interfejsu, którą przechowuje wewnątrz wywoływanych otok środowiska uruchomieniowego (RCW).</span><span class="sxs-lookup"><span data-stu-id="a335f-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="a335f-104">To powoduje zwolnienie wszystkich RCW pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="a335f-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="a335f-105">Ta funkcja globalna jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a335f-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a335f-106">Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a335f-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a335f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a335f-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a335f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a335f-108">Remarks</span></span>  
 <span data-ttu-id="a335f-109">`CoEEShutDownCOM` Funkcji najpierw zwalnia RCW we wszystkich kontekstach i wszystkich pamięci podręcznych, a następnie usuwa wszelkie powiadomienia zakończenia istniejące w Instalatorze.</span><span class="sxs-lookup"><span data-stu-id="a335f-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="a335f-110">Nie zwalnianie biblioteki DLL występuje.</span><span class="sxs-lookup"><span data-stu-id="a335f-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a335f-111">Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="a335f-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="a335f-112">Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], wywołać punkt wejścia dla tej funkcji, od określonego środowiska uruchomieniowego, chcesz mieć wpływ.</span><span class="sxs-lookup"><span data-stu-id="a335f-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="a335f-113">Aby uzyskać punkt wejścia, należy wywołać [iclrruntimeinfo::GetProcAddress —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodę i określić "coeeshutdowncom —".</span><span class="sxs-lookup"><span data-stu-id="a335f-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a335f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a335f-114">Requirements</span></span>  
 <span data-ttu-id="a335f-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a335f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a335f-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a335f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a335f-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a335f-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a335f-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a335f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a335f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a335f-119">See also</span></span>
- [<span data-ttu-id="a335f-120">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="a335f-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
