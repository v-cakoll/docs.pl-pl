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
ms.openlocfilehash: 2ff1f9428a92d091a51a4cca12d69d98da0ecba2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120536"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="11706-102">ICLRProbingAssemblyEnum::Get — Metoda</span><span class="sxs-lookup"><span data-stu-id="11706-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="11706-103">Pobiera tożsamość zestawu o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="11706-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11706-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11706-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11706-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11706-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="11706-106">podczas Indeks (liczony od zera) tożsamości zestawu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="11706-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="11706-107">określoną Bufor zawierający dane tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="11706-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="11706-108">[in. out] Rozmiar buforu `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="11706-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11706-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11706-109">Return Value</span></span>  
  
|<span data-ttu-id="11706-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11706-110">HRESULT</span></span>|<span data-ttu-id="11706-111">Opis</span><span class="sxs-lookup"><span data-stu-id="11706-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11706-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="11706-112">S_OK</span></span>|<span data-ttu-id="11706-113">`Get` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="11706-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="11706-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="11706-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="11706-115">`pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="11706-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="11706-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="11706-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="11706-117">Wyliczenie nie zawiera żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="11706-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="11706-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11706-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11706-119">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="11706-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11706-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11706-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11706-121">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="11706-121">The call timed out.</span></span>|  
|<span data-ttu-id="11706-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11706-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11706-123">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="11706-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11706-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11706-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11706-125">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="11706-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11706-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11706-126">E_FAIL</span></span>|<span data-ttu-id="11706-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="11706-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11706-128">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="11706-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11706-129">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11706-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11706-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11706-130">Remarks</span></span>  
 <span data-ttu-id="11706-131">Tożsamość pod indeksem 0 jest tożsamością specyficzną dla architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="11706-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="11706-132">Tożsamość pod indeksem 1 to zestaw neutralny od architektury dla języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="11706-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="11706-133">Tożsamość pod indeksem 2 nie zawiera informacji o architekturze.</span><span class="sxs-lookup"><span data-stu-id="11706-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="11706-134">`Get` jest zazwyczaj wywoływana dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="11706-134">`Get` is typically called twice.</span></span> <span data-ttu-id="11706-135">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`i ustawia `pcchBufferSize` do rozmiaru właściwego dla `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="11706-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="11706-136">Drugie wywołanie dostarcza odpowiednio przyznany rozmiar `pwzBuffer`i zawiera dane tożsamości zestawu kanonicznego po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="11706-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11706-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11706-137">Requirements</span></span>  
 <span data-ttu-id="11706-138">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11706-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11706-139">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="11706-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11706-140">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11706-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11706-141">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11706-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11706-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11706-142">See also</span></span>

- [<span data-ttu-id="11706-143">ICLRProbingAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="11706-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="11706-144">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="11706-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
