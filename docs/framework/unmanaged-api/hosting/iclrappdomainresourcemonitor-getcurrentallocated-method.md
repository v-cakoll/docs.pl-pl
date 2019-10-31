---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
ms.openlocfilehash: f19ac39737d08c10c23ce0bde03131f52b660cac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126813"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="a4b7e-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated — Metoda</span><span class="sxs-lookup"><span data-stu-id="a4b7e-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="a4b7e-103">Pobiera łączny rozmiar (w bajtach) wszystkich alokacji pamięci wykonanych przez domenę aplikacji od momentu utworzenia, bez odejmowania pamięci, która została zebrana jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a4b7e-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4b7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4b7e-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="a4b7e-106">podczas Identyfikator żądanej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4b7e-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="a4b7e-107">określoną Wskaźnik do całkowitego rozmiaru wszystkich alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="a4b7e-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4b7e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a4b7e-108">Return Value</span></span>  
 <span data-ttu-id="a4b7e-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a4b7e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a4b7e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4b7e-110">HRESULT</span></span>|<span data-ttu-id="a4b7e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a4b7e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4b7e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4b7e-112">S_OK</span></span>|<span data-ttu-id="a4b7e-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a4b7e-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="a4b7e-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="a4b7e-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="a4b7e-115">Domena aplikacji została zwolniona lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a4b7e-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4b7e-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4b7e-116">Remarks</span></span>  
 <span data-ttu-id="a4b7e-117">Ta metoda jest niezarządzanym odpowiednikiem właściwości Managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a4b7e-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b7e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4b7e-118">Requirements</span></span>  
 <span data-ttu-id="a4b7e-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4b7e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b7e-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="a4b7e-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a4b7e-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a4b7e-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4b7e-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b7e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b7e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4b7e-123">See also</span></span>

- [<span data-ttu-id="a4b7e-124">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="a4b7e-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="a4b7e-125">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="a4b7e-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="a4b7e-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a4b7e-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a4b7e-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="a4b7e-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
