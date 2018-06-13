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
ms.openlocfilehash: d8cfb2f18bcceed3a125ac7876122c02d2267698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436458"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="d78e2-102">ICLRReferenceAssemblyEnum::Get — Metoda</span><span class="sxs-lookup"><span data-stu-id="d78e2-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="d78e2-103">Pobiera tożsamość zestawu o indeksie dostarczony.</span><span class="sxs-lookup"><span data-stu-id="d78e2-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d78e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d78e2-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d78e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d78e2-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="d78e2-106">[in] Liczony od zera indeks tożsamości zestawu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d78e2-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="d78e2-107">[out] Bufor zawierający dane tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="d78e2-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="d78e2-108">[w, out] Rozmiar `pwzBuffer` buforu.</span><span class="sxs-lookup"><span data-stu-id="d78e2-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d78e2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d78e2-109">Return Value</span></span>  
  
|<span data-ttu-id="d78e2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d78e2-110">HRESULT</span></span>|<span data-ttu-id="d78e2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d78e2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d78e2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d78e2-112">S_OK</span></span>|<span data-ttu-id="d78e2-113">`Get` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d78e2-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="d78e2-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d78e2-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d78e2-115">`pwzBuffer` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="d78e2-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="d78e2-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="d78e2-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="d78e2-117">Wyliczanie nie zawiera więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="d78e2-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="d78e2-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d78e2-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d78e2-119">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d78e2-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d78e2-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d78e2-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d78e2-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d78e2-121">The call timed out.</span></span>|  
|<span data-ttu-id="d78e2-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d78e2-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d78e2-123">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d78e2-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d78e2-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d78e2-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d78e2-125">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d78e2-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d78e2-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d78e2-126">E_FAIL</span></span>|<span data-ttu-id="d78e2-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d78e2-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d78e2-128">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d78e2-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d78e2-129">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d78e2-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d78e2-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d78e2-130">Remarks</span></span>  
 <span data-ttu-id="d78e2-131">`Get` jest zazwyczaj wywoływana dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="d78e2-131">`Get` is typically called twice.</span></span> <span data-ttu-id="d78e2-132">Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer`i ustawia `pcchBufferSize` odpowiednie dla rozmiaru `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d78e2-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="d78e2-133">Drugie wywołanie dostarcza odpowiednio rozmiarze `pwzBuffer`i zawiera dane tożsamości zestawu canonical po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="d78e2-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d78e2-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d78e2-134">Requirements</span></span>  
 <span data-ttu-id="d78e2-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d78e2-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d78e2-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d78e2-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d78e2-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d78e2-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d78e2-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d78e2-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78e2-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d78e2-139">See Also</span></span>  
 [<span data-ttu-id="d78e2-140">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="d78e2-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d78e2-141">ICLRReferenceAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="d78e2-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
