---
title: ICLRReferenceAssemblyEnum::Get — Metoda
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d26ed6249bad8a7e2fbaab01264c1b32e1ff55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638661"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="9be0d-102">ICLRReferenceAssemblyEnum::Get — Metoda</span><span class="sxs-lookup"><span data-stu-id="9be0d-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="9be0d-103">Pobiera tożsamość zestawu o podany indeks.</span><span class="sxs-lookup"><span data-stu-id="9be0d-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9be0d-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9be0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9be0d-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="9be0d-106">[in] Liczony od zera indeks tożsamości zestawu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="9be0d-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="9be0d-107">[out] Bufor, zawierająca dane tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="9be0d-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="9be0d-108">[out w] Rozmiar `pwzBuffer` buforu.</span><span class="sxs-lookup"><span data-stu-id="9be0d-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9be0d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9be0d-109">Return Value</span></span>  
  
|<span data-ttu-id="9be0d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9be0d-110">HRESULT</span></span>|<span data-ttu-id="9be0d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9be0d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9be0d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9be0d-112">S_OK</span></span>|<span data-ttu-id="9be0d-113">`Get` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="9be0d-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="9be0d-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9be0d-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9be0d-115">`pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="9be0d-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="9be0d-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="9be0d-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="9be0d-117">Wyliczenia nie zawiera więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="9be0d-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="9be0d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9be0d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9be0d-119">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9be0d-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9be0d-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9be0d-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9be0d-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="9be0d-121">The call timed out.</span></span>|  
|<span data-ttu-id="9be0d-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9be0d-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9be0d-123">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="9be0d-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9be0d-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9be0d-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9be0d-125">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="9be0d-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9be0d-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9be0d-126">E_FAIL</span></span>|<span data-ttu-id="9be0d-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9be0d-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9be0d-128">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="9be0d-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9be0d-129">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9be0d-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9be0d-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9be0d-130">Remarks</span></span>  
 <span data-ttu-id="9be0d-131">`Get` jest zazwyczaj wywoływana dwa razy.</span><span class="sxs-lookup"><span data-stu-id="9be0d-131">`Get` is typically called twice.</span></span> <span data-ttu-id="9be0d-132">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`i ustawia `pcchBufferSize` odpowiedni dla rozmiaru `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9be0d-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="9be0d-133">Drugie wywołanie dostarcza właściwy rozmiar `pwzBuffer`i zawiera dane tożsamości zestawu canonical po jego ukończeniu.</span><span class="sxs-lookup"><span data-stu-id="9be0d-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9be0d-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9be0d-134">Requirements</span></span>  
 <span data-ttu-id="9be0d-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9be0d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be0d-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9be0d-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9be0d-137">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9be0d-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9be0d-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9be0d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be0d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9be0d-139">See also</span></span>

- [<span data-ttu-id="9be0d-140">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="9be0d-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9be0d-141">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="9be0d-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
