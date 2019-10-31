---
title: ICLRValidator::FormatEventInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
ms.openlocfilehash: 935d8e9fa3ed15be03c6cd05b1bc3c4919d0cc2b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127853"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="6b89d-102">ICLRValidator::FormatEventInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b89d-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="6b89d-103">Pobiera szczegółowy komunikat o określonym błędzie walidacji.</span><span class="sxs-lookup"><span data-stu-id="6b89d-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b89d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b89d-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b89d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b89d-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="6b89d-106">podczas Wartość HRESULT, która została przeniesiona do procedury obsługi błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="6b89d-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="6b89d-107">podczas Wystąpienie `VEContext`, które zawiera informacje o kontekście błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="6b89d-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="6b89d-108">[in. out] Przyjazny komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="6b89d-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="6b89d-109">podczas Maksymalna długość komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="6b89d-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="6b89d-110">podczas Bezpieczna tablica dodatkowych parametrów do użycia w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="6b89d-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b89d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b89d-111">Return Value</span></span>  
  
|<span data-ttu-id="6b89d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b89d-112">HRESULT</span></span>|<span data-ttu-id="6b89d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6b89d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b89d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b89d-114">S_OK</span></span>|<span data-ttu-id="6b89d-115">`FormatEventInfo` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="6b89d-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="6b89d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b89d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b89d-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b89d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b89d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b89d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b89d-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6b89d-119">The call timed out.</span></span>|  
|<span data-ttu-id="6b89d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b89d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b89d-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6b89d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b89d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b89d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b89d-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="6b89d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b89d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b89d-124">E_FAIL</span></span>|<span data-ttu-id="6b89d-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6b89d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b89d-126">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="6b89d-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b89d-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b89d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b89d-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b89d-128">Requirements</span></span>  
 <span data-ttu-id="6b89d-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b89d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b89d-130">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="6b89d-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6b89d-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b89d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b89d-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b89d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b89d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b89d-133">See also</span></span>

- [<span data-ttu-id="6b89d-134">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b89d-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="6b89d-135">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b89d-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
