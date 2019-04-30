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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9117a82dff48dcda8d96f0feb7b8c4a001fa17f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763325"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="582df-102">ICLRValidator::FormatEventInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="582df-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="582df-103">Pobiera szczegółowy komunikat o błędzie sprawdzania poprawności określonej.</span><span class="sxs-lookup"><span data-stu-id="582df-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="582df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="582df-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="582df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="582df-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="582df-106">[in] Wartość HRESULT, który został przekazany do procedury obsługi błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="582df-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="582df-107">[in] A `VEContext` wystąpienia, które zawiera informacje o kontekście dotyczące błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="582df-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="582df-108">[out w] Przyjazny komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="582df-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="582df-109">[in] Maksymalna długość komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="582df-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="582df-110">[in] Bezpieczną tablicą dodatkowych parametrów do użycia w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="582df-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="582df-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="582df-111">Return Value</span></span>  
  
|<span data-ttu-id="582df-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="582df-112">HRESULT</span></span>|<span data-ttu-id="582df-113">Opis</span><span class="sxs-lookup"><span data-stu-id="582df-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="582df-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="582df-114">S_OK</span></span>|<span data-ttu-id="582df-115">`FormatEventInfo` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="582df-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="582df-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="582df-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="582df-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="582df-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="582df-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="582df-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="582df-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="582df-119">The call timed out.</span></span>|  
|<span data-ttu-id="582df-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="582df-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="582df-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="582df-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="582df-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="582df-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="582df-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="582df-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="582df-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="582df-124">E_FAIL</span></span>|<span data-ttu-id="582df-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="582df-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="582df-126">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="582df-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="582df-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="582df-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="582df-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="582df-128">Requirements</span></span>  
 <span data-ttu-id="582df-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="582df-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="582df-130">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="582df-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="582df-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="582df-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="582df-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="582df-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582df-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="582df-133">See also</span></span>

- [<span data-ttu-id="582df-134">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="582df-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="582df-135">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="582df-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
