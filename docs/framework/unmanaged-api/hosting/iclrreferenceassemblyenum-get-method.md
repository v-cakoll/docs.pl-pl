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
ms.openlocfilehash: 8f479443e168c3fc7c627c3227e59f1e8b54f0e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120505"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="87671-102">ICLRReferenceAssemblyEnum::Get — Metoda</span><span class="sxs-lookup"><span data-stu-id="87671-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="87671-103">Pobiera tożsamość zestawu przy użyciu podanego indeksu.</span><span class="sxs-lookup"><span data-stu-id="87671-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87671-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87671-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87671-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87671-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="87671-106">podczas Indeks (liczony od zera) tożsamości zestawu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="87671-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="87671-107">określoną Bufor zawierający dane tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="87671-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="87671-108">[in. out] Rozmiar buforu `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="87671-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87671-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87671-109">Return Value</span></span>  
  
|<span data-ttu-id="87671-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87671-110">HRESULT</span></span>|<span data-ttu-id="87671-111">Opis</span><span class="sxs-lookup"><span data-stu-id="87671-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87671-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="87671-112">S_OK</span></span>|<span data-ttu-id="87671-113">`Get` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="87671-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="87671-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="87671-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="87671-115">`pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="87671-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="87671-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="87671-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="87671-117">Wyliczenie nie zawiera żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="87671-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="87671-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87671-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87671-119">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="87671-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="87671-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="87671-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="87671-121">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="87671-121">The call timed out.</span></span>|  
|<span data-ttu-id="87671-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="87671-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="87671-123">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="87671-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="87671-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="87671-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="87671-125">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="87671-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="87671-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87671-126">E_FAIL</span></span>|<span data-ttu-id="87671-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="87671-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="87671-128">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="87671-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="87671-129">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="87671-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87671-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87671-130">Remarks</span></span>  
 <span data-ttu-id="87671-131">`Get` jest zazwyczaj wywoływana dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="87671-131">`Get` is typically called twice.</span></span> <span data-ttu-id="87671-132">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`i ustawia `pcchBufferSize` do rozmiaru właściwego dla `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="87671-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="87671-133">Drugie wywołanie dostarcza odpowiednio przyznany rozmiar `pwzBuffer`i zawiera dane tożsamości zestawu kanonicznego po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="87671-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87671-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87671-134">Requirements</span></span>  
 <span data-ttu-id="87671-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87671-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87671-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="87671-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87671-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87671-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87671-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87671-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87671-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87671-139">See also</span></span>

- [<span data-ttu-id="87671-140">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="87671-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="87671-141">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="87671-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
