---
title: ICLRMetaHost::EnumerateInstalledRuntimes — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ed4c09d910db6fa2e61d44e4ac777f9b6095a20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="049f9-102">ICLRMetaHost::EnumerateInstalledRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="049f9-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="049f9-103">Zwraca wyliczenie, który zawiera prawidłowy [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs dla każdej wersji środowisko uruchomieniowe języka wspólnego (CLR) jest zainstalowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="049f9-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="049f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="049f9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="049f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="049f9-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="049f9-106">[out] Wyliczenie [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsy odpowiadający każdej wersji środowiska CLR, która jest zainstalowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="049f9-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="049f9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="049f9-107">Return Value</span></span>  
 <span data-ttu-id="049f9-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="049f9-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="049f9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="049f9-109">HRESULT</span></span>|<span data-ttu-id="049f9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="049f9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="049f9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="049f9-111">S_OK</span></span>|<span data-ttu-id="049f9-112">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="049f9-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="049f9-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="049f9-113">E_POINTER</span></span>|<span data-ttu-id="049f9-114">`ppEnumerator` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="049f9-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="049f9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="049f9-115">Requirements</span></span>  
 <span data-ttu-id="049f9-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="049f9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="049f9-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="049f9-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="049f9-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="049f9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="049f9-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="049f9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="049f9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="049f9-120">See Also</span></span>  
 [<span data-ttu-id="049f9-121">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="049f9-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="049f9-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="049f9-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
