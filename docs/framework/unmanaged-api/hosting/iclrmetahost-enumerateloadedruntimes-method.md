---
title: ICLRMetaHost::EnumerateLoadedRuntimes — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 2e22b8a2d0213b3bd766d80218d6f396721a90e1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703767"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="7fdc9-102">ICLRMetaHost::EnumerateLoadedRuntimes — Metoda</span><span class="sxs-lookup"><span data-stu-id="7fdc9-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="7fdc9-103">Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) dla każdej wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany w danym procesie.</span><span class="sxs-lookup"><span data-stu-id="7fdc9-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="7fdc9-104">Ta metoda zastępuje funkcję [GetVersionFromProcess —](getversionfromprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7fdc9-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fdc9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fdc9-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fdc9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fdc9-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="7fdc9-107">podczas Dojście procesu do sprawdzenia pod kątem załadowanych środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7fdc9-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="7fdc9-108">określoną <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>Wyliczenie interfejsów [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) odpowiadających każdemu CLR, który jest ładowany przez proces.</span><span class="sxs-lookup"><span data-stu-id="7fdc9-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fdc9-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7fdc9-109">Return Value</span></span>  
 <span data-ttu-id="7fdc9-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="7fdc9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7fdc9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fdc9-111">HRESULT</span></span>|<span data-ttu-id="7fdc9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7fdc9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fdc9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fdc9-113">S_OK</span></span>|<span data-ttu-id="7fdc9-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7fdc9-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7fdc9-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7fdc9-115">E_POINTER</span></span>|<span data-ttu-id="7fdc9-116">`ppEnumerator`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="7fdc9-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fdc9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fdc9-117">Remarks</span></span>  
 <span data-ttu-id="7fdc9-118">Ta metoda zawiera wszystkie załadowane środowiska uruchomieniowe, nawet jeśli zostały załadowane przy użyciu przestarzałych funkcji, takich jak [CorBindToRuntime](corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="7fdc9-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fdc9-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fdc9-119">Requirements</span></span>  
 <span data-ttu-id="7fdc9-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fdc9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fdc9-121">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="7fdc9-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7fdc9-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7fdc9-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fdc9-123">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fdc9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fdc9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fdc9-124">See also</span></span>

- [<span data-ttu-id="7fdc9-125">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="7fdc9-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="7fdc9-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="7fdc9-126">Hosting</span></span>](index.md)
