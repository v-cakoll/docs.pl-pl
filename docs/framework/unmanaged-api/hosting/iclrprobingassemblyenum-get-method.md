---
title: ICLRProbingAssemblyEnum::Get — Metoda
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 268462db51435b87194aafc374d5d8e8ec1df165
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638654"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="6f30e-102">ICLRProbingAssemblyEnum::Get — Metoda</span><span class="sxs-lookup"><span data-stu-id="6f30e-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="6f30e-103">Pobiera tożsamość zestawu pod określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="6f30e-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f30e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f30e-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f30e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f30e-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="6f30e-106">[in] Liczony od zera indeks tożsamości zestawu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="6f30e-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="6f30e-107">[out] Bufor, zawierająca dane tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="6f30e-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="6f30e-108">[out w] Rozmiar `pwzBuffer` buforu.</span><span class="sxs-lookup"><span data-stu-id="6f30e-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f30e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6f30e-109">Return Value</span></span>  
  
|<span data-ttu-id="6f30e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f30e-110">HRESULT</span></span>|<span data-ttu-id="6f30e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6f30e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f30e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f30e-112">S_OK</span></span>|<span data-ttu-id="6f30e-113">`Get` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6f30e-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="6f30e-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6f30e-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6f30e-115">`pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="6f30e-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="6f30e-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="6f30e-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="6f30e-117">Wyliczenia nie zawiera więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="6f30e-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="6f30e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f30e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f30e-119">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6f30e-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f30e-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f30e-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f30e-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6f30e-121">The call timed out.</span></span>|  
|<span data-ttu-id="6f30e-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f30e-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f30e-123">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="6f30e-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f30e-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f30e-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f30e-125">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6f30e-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f30e-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f30e-126">E_FAIL</span></span>|<span data-ttu-id="6f30e-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6f30e-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f30e-128">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6f30e-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f30e-129">Kolejne wywołania metody hostowania Zwróć HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f30e-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f30e-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f30e-130">Remarks</span></span>  
 <span data-ttu-id="6f30e-131">Tożsamość pod indeksem 0 jest tożsamość specyficzne dla architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="6f30e-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="6f30e-132">Tożsamość pod indeksem 1 jest architektura neutralny dla języka Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="6f30e-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="6f30e-133">Tożsamość pod indeksem 2 nie zawiera żadnych informacji architektury.</span><span class="sxs-lookup"><span data-stu-id="6f30e-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="6f30e-134">`Get` jest zazwyczaj wywoływana dwa razy.</span><span class="sxs-lookup"><span data-stu-id="6f30e-134">`Get` is typically called twice.</span></span> <span data-ttu-id="6f30e-135">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`i ustawia `pcchBufferSize` odpowiedni dla rozmiaru `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6f30e-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="6f30e-136">Drugie wywołanie dostarcza właściwy rozmiar `pwzBuffer`i zawiera dane tożsamości zestawu canonical po jego ukończeniu.</span><span class="sxs-lookup"><span data-stu-id="6f30e-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f30e-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f30e-137">Requirements</span></span>  
 <span data-ttu-id="6f30e-138">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f30e-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f30e-139">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f30e-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f30e-140">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f30e-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f30e-141">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f30e-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f30e-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f30e-142">See also</span></span>

- [<span data-ttu-id="6f30e-143">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f30e-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="6f30e-144">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f30e-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
