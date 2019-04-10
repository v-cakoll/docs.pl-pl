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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205878"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="a1595-102">ICLRValidator::FormatEventInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1595-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="a1595-103">Pobiera szczegółowy komunikat o błędzie sprawdzania poprawności określonej.</span><span class="sxs-lookup"><span data-stu-id="a1595-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1595-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1595-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1595-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1595-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="a1595-106">[in] Wartość HRESULT, który został przekazany do procedury obsługi błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="a1595-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="a1595-107">[in] A `VEContext` wystąpienia, które zawiera informacje o kontekście dotyczące błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="a1595-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="a1595-108">[out w] Przyjazny komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a1595-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="a1595-109">[in] Maksymalna długość komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a1595-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="a1595-110">[in] Bezpieczną tablicą dodatkowych parametrów do użycia w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a1595-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1595-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1595-111">Return Value</span></span>  
  
|<span data-ttu-id="a1595-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1595-112">HRESULT</span></span>|<span data-ttu-id="a1595-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a1595-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1595-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1595-114">S_OK</span></span>|`FormatEventInfo` <span data-ttu-id="a1595-115">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a1595-115">returned successfully.</span></span>|  
|<span data-ttu-id="a1595-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1595-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1595-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a1595-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1595-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1595-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1595-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a1595-119">The call timed out.</span></span>|  
|<span data-ttu-id="a1595-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1595-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1595-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a1595-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1595-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1595-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1595-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a1595-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1595-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1595-124">E_FAIL</span></span>|<span data-ttu-id="a1595-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a1595-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1595-126">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a1595-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1595-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a1595-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1595-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1595-128">Requirements</span></span>  
 <span data-ttu-id="a1595-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1595-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1595-130">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="a1595-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a1595-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1595-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a1595-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a1595-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1595-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1595-133">See also</span></span>

- [<span data-ttu-id="a1595-134">ICLRErrorReportingManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a1595-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="a1595-135">ICLRValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a1595-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
