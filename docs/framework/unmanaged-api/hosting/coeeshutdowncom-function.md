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
ms.openlocfilehash: 6a28b9d6e41d0572d423576f5b4024a60a70216c
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456861"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="5de8d-102">CoEEShutDownCOM — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5de8d-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="5de8d-103">Wymusza środowisko uruchomieniowe języka wspólnego (CLR), aby zwolnić wszystkie wskaźniki interfejsu, którą przechowuje wewnątrz wywoływanych otok środowiska uruchomieniowego (RCW).</span><span class="sxs-lookup"><span data-stu-id="5de8d-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="5de8d-104">To powoduje zwolnienie wszystkich RCW pamięci podręcznych.</span><span class="sxs-lookup"><span data-stu-id="5de8d-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="5de8d-105">Ta funkcja globalna jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5de8d-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="5de8d-106">Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5de8d-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5de8d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5de8d-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5de8d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5de8d-108">Remarks</span></span>  
 <span data-ttu-id="5de8d-109">`CoEEShutDownCOM` Funkcji najpierw zwalnia RCW we wszystkich kontekstach i wszystkich pamięci podręcznych, a następnie usuwa wszelkie powiadomienia zakończenia istniejące w Instalatorze.</span><span class="sxs-lookup"><span data-stu-id="5de8d-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="5de8d-110">Nie zwalnianie biblioteki DLL występuje.</span><span class="sxs-lookup"><span data-stu-id="5de8d-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5de8d-111">Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="5de8d-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="5de8d-112">Począwszy od programu .NET Framework 4, należy wywołać punkt wejścia dla tej funkcji, od określonego środowiska uruchomieniowego, które mają wpływ na.</span><span class="sxs-lookup"><span data-stu-id="5de8d-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="5de8d-113">Aby uzyskać punkt wejścia, należy wywołać [iclrruntimeinfo::GetProcAddress —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodę i określić "coeeshutdowncom —".</span><span class="sxs-lookup"><span data-stu-id="5de8d-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5de8d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5de8d-114">Requirements</span></span>  
 <span data-ttu-id="5de8d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5de8d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5de8d-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5de8d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5de8d-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5de8d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5de8d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5de8d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5de8d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5de8d-119">See also</span></span>

- [<span data-ttu-id="5de8d-120">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="5de8d-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
