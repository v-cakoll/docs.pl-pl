---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 648a2c044920b7524ad96ff656e83268ffd55652
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612219"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="bfd9d-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived — Metoda</span><span class="sxs-lookup"><span data-stu-id="bfd9d-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="bfd9d-103">Pobiera liczbę bajtów, które przetrwały ostatniej pełnej, blokowanie wyrzucania elementów bezużytecznych i które są przywoływane przez bieżącej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfd9d-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfd9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfd9d-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="bfd9d-106">[in] Identyfikator domeny żądanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="bfd9d-107">[out] Wskaźnik do liczby bajtów, które przetrwały po ostatnim wyrzucania elementów bezużytecznych, które są przechowywane w tej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="bfd9d-108">Po pełnego ta liczba jest dokładne i kompletne.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="bfd9d-109">Po pobraniu tymczasowych ta liczba jest potencjalnie niekompletne.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="bfd9d-110">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="bfd9d-111">[out] Wskaźnik do całkowita liczba bajtów, które przetrwały od ostatniego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="bfd9d-112">Po pełnego ta wartość liczbowa określa liczbę bajtów, które są przechowywane w zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="bfd9d-113">Po pobraniu tymczasowych ta wartość liczbowa określa liczbę bajtów, które są przechowywane na żywo w generacje efemeryczne.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="bfd9d-114">Ten parametr może być `null`.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfd9d-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bfd9d-115">Return Value</span></span>  
 <span data-ttu-id="bfd9d-116">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bfd9d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bfd9d-117">HRESULT</span></span>|<span data-ttu-id="bfd9d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bfd9d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bfd9d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="bfd9d-119">S_OK</span></span>|<span data-ttu-id="bfd9d-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="bfd9d-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="bfd9d-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="bfd9d-122">Domeny aplikacji został zwolniony lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfd9d-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfd9d-123">Remarks</span></span>  
 <span data-ttu-id="bfd9d-124">Statystyki są aktualizowane tylko po pełnej, blokowanie wyrzucania elementów bezużytecznych; oznacza to, że występuje kolekcję zawierającą wszystkie generacje i który zatrzymuje aplikację podczas zbierania.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="bfd9d-125">Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenie metody wykonywania pełnego, blokowanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="bfd9d-126">Współbieżne wyrzucanie elementów bezużytecznych występuje w tle i nie są blokowane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="bfd9d-127">`GetCurrentSurvived` Metody odpowiada niezarządzanych zarządzaną <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bfd9d-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfd9d-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfd9d-128">Requirements</span></span>  
 <span data-ttu-id="bfd9d-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfd9d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfd9d-130">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bfd9d-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bfd9d-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bfd9d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfd9d-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfd9d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd9d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfd9d-133">See also</span></span>
- [<span data-ttu-id="bfd9d-134">ICLRAppDomainResourceMonitor, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfd9d-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="bfd9d-135">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="bfd9d-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="bfd9d-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bfd9d-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="bfd9d-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="bfd9d-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
