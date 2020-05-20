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
ms.openlocfilehash: a73c0731c79dea3a0c411fe27a864ec9ac4e20b2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616024"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="08d30-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived — Metoda</span><span class="sxs-lookup"><span data-stu-id="08d30-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="08d30-103">Pobiera liczbę bajtów, które przeżyły ostatnią pełną, blokującą wyrzucanie elementów bezużytecznych i przywoływanych przez bieżącą domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08d30-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08d30-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08d30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08d30-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="08d30-106">podczas Identyfikator żądanej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08d30-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="08d30-107">określoną Wskaźnik do liczby bajtów przeprowadzonych po ostatnim wyrzucaniu elementów bezużytecznych przechowywanych przez tę domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08d30-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="08d30-108">Po pełnej kolekcji ta liczba jest dokładna i kompletna.</span><span class="sxs-lookup"><span data-stu-id="08d30-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="08d30-109">Po zakończeniu zbierania danych tymczasowych ten numer jest potencjalnie niekompletny.</span><span class="sxs-lookup"><span data-stu-id="08d30-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="08d30-110">Ten parametr może być `null` .</span><span class="sxs-lookup"><span data-stu-id="08d30-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="08d30-111">określoną Wskaźnik do łącznej liczby bajtów przeczytanych z ostatniego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="08d30-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="08d30-112">Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów przechowywanych w stertach zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="08d30-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="08d30-113">Po zbiorze tymczasowych ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w generacjach tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="08d30-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="08d30-114">Ten parametr może być `null` .</span><span class="sxs-lookup"><span data-stu-id="08d30-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08d30-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="08d30-115">Return Value</span></span>  
 <span data-ttu-id="08d30-116">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="08d30-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="08d30-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08d30-117">HRESULT</span></span>|<span data-ttu-id="08d30-118">Opis</span><span class="sxs-lookup"><span data-stu-id="08d30-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08d30-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="08d30-119">S_OK</span></span>|<span data-ttu-id="08d30-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="08d30-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="08d30-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="08d30-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="08d30-122">Domena aplikacji została zwolniona lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="08d30-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d30-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08d30-123">Remarks</span></span>  
 <span data-ttu-id="08d30-124">Statystyki są aktualizowane tylko po pełnej, blokującej wyrzucaniu elementów bezużytecznych; oznacza to, że kolekcja obejmująca wszystkie generacje i która zatrzyma aplikację podczas zbierania.</span><span class="sxs-lookup"><span data-stu-id="08d30-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="08d30-125">Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> Przeciążenie metody wykonuje pełną, blokującą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="08d30-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="08d30-126">Współbieżne wyrzucanie elementów bezużytecznych odbywa się w tle i nie blokuje aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08d30-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="08d30-127">`GetCurrentSurvived`Metoda jest niezarządzanym odpowiednikiem właściwości zarządzanej <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08d30-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d30-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08d30-128">Requirements</span></span>  
 <span data-ttu-id="08d30-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d30-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d30-130">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="08d30-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="08d30-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08d30-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08d30-132">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d30-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d30-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08d30-133">See also</span></span>

- [<span data-ttu-id="08d30-134">ICLRAppDomainResourceMonitor — Interfejs</span><span class="sxs-lookup"><span data-stu-id="08d30-134">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="08d30-135">Monitorowanie zasobów domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="08d30-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="08d30-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="08d30-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="08d30-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="08d30-137">Hosting</span></span>](index.md)
