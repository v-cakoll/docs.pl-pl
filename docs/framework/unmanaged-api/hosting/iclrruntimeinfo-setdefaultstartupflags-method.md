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
ms.openlocfilehash: 7d201962976d198372226eb686696fcdccf3eb69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762165"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="9d194-102">ICLRRuntimeInfo::SetDefaultStartupFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d194-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="9d194-103">Ustawia flagi uruchamiania i plik konfiguracji hosta, który zostanie użyty do uruchomienia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9d194-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="9d194-104">Ta metoda zastępuje użycie `startupFlags` parametru w funkcjach [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [CorBindToRuntimeHost —](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9d194-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d194-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d194-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d194-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d194-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="9d194-107">podczas Flagi uruchamiania hosta do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="9d194-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="9d194-108">Użyj tych samych flag co w przypadku funkcji [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [CorBindToRuntimeHost —](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9d194-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="9d194-109">podczas Ścieżka katalogu pliku konfiguracji hosta do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="9d194-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d194-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d194-110">Return Value</span></span>  
 <span data-ttu-id="9d194-111">Ta metoda zwraca następujące określone wartości HRESULT, a także błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9d194-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9d194-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d194-112">HRESULT</span></span>|<span data-ttu-id="9d194-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9d194-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d194-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d194-114">S_OK</span></span>|<span data-ttu-id="9d194-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9d194-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d194-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d194-116">Remarks</span></span>  
 <span data-ttu-id="9d194-117">Host wielowątkowy powinien synchronizować wywołania z tą metodą.</span><span class="sxs-lookup"><span data-stu-id="9d194-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="9d194-118">W przeciwnym razie wątek A może wywoływać `SetStartupFlags` metodę po zakończeniu wątku b zakończy wywołanie do `SetStartupFlags` i zanim wątek b uruchomi środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="9d194-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d194-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d194-119">Requirements</span></span>  
 <span data-ttu-id="9d194-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d194-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d194-121">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="9d194-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d194-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d194-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d194-123">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d194-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d194-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d194-124">See also</span></span>

- [<span data-ttu-id="9d194-125">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d194-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9d194-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9d194-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9d194-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="9d194-127">Hosting</span></span>](index.md)
