---
title: ICLRRuntimeInfo::SetDefaultStartupFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3174cf3b4f4f4ac4b2c8e69030357eb1e46cf3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197831"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="e1fb6-102">ICLRRuntimeInfo::SetDefaultStartupFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1fb6-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="e1fb6-103">Ustawia flagi uruchamiania i pliku konfiguracyjnego hosta, która będzie służyć do uruchomienia w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="e1fb6-104">Ta metoda zastępuje użycia `startupFlags` parametru w [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [corbindtoruntimehost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1fb6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1fb6-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1fb6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1fb6-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="e1fb6-107">[in] Flagi uruchamiania hosta można ustawić.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="e1fb6-108">Za pomocą tego samego flag jako za pomocą [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [corbindtoruntimehost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="e1fb6-109">[in] Ścieżka katalogu pliku konfiguracyjnego hosta, aby ustawić.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1fb6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e1fb6-110">Return Value</span></span>  
 <span data-ttu-id="e1fb6-111">Ta metoda zwraca następujące HRESULT określonych oraz błędów HRESULT, wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e1fb6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1fb6-112">HRESULT</span></span>|<span data-ttu-id="e1fb6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e1fb6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1fb6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1fb6-114">S_OK</span></span>|<span data-ttu-id="e1fb6-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1fb6-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1fb6-116">Remarks</span></span>  
 <span data-ttu-id="e1fb6-117">Wielowątkowe hosta należy synchronizować wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="e1fb6-118">W przeciwnym razie wątek A mogą wywołać `SetStartupFlags` metody, gdy wątek B zakończy się po wywołaniu `SetStartupFlags` i przed wątku B uruchamia środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="e1fb6-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1fb6-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1fb6-119">Requirements</span></span>  
 <span data-ttu-id="e1fb6-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1fb6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1fb6-121">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e1fb6-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e1fb6-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1fb6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e1fb6-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e1fb6-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1fb6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1fb6-124">See also</span></span>

- [<span data-ttu-id="e1fb6-125">ICLRRuntimeInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e1fb6-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e1fb6-126">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e1fb6-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e1fb6-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="e1fb6-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
