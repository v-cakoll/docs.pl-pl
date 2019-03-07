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
ms.openlocfilehash: 900ad908229b7881dfa9ba55732e20926c912d7c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469082"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="53990-102">ICLRMetaHost::EnumerateInstalledRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="53990-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="53990-103">Zwraca wyliczenie, które zawiera prawidłową [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs dla każdej wersji programu środowisko uruchomieniowe języka wspólnego (CLR) jest zainstalowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="53990-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53990-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53990-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53990-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53990-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="53990-106">[out] Wyliczenie [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsów odpowiadający każdej wersji środowiska CLR, który jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="53990-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53990-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53990-107">Return Value</span></span>  
 <span data-ttu-id="53990-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="53990-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="53990-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53990-109">HRESULT</span></span>|<span data-ttu-id="53990-110">Opis</span><span class="sxs-lookup"><span data-stu-id="53990-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53990-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="53990-111">S_OK</span></span>|<span data-ttu-id="53990-112">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="53990-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="53990-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="53990-113">E_POINTER</span></span>|<span data-ttu-id="53990-114">`ppEnumerator` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="53990-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53990-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53990-115">Requirements</span></span>  
 <span data-ttu-id="53990-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53990-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53990-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="53990-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="53990-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53990-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53990-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53990-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53990-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53990-120">See also</span></span>
- [<span data-ttu-id="53990-121">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="53990-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="53990-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="53990-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
