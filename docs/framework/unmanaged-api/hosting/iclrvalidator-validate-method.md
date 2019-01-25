---
title: ICLRValidator::Validate — Metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccd6dbe63f02fa7e28c6aec1be815f1f1967a90a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718731"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="739ba-102">ICLRValidator::Validate — Metoda</span><span class="sxs-lookup"><span data-stu-id="739ba-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="739ba-103">Sprawdza poprawność pliku wykonalnego (PE) lub języka Microsoft intermediate language (MSIL) w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="739ba-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="739ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="739ba-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
#### <a name="parameters"></a><span data-ttu-id="739ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="739ba-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="739ba-106">[in] Wskaźnik do `IVEHandler` wystąpienia, która obsługuje błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="739ba-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="739ba-107">[in] Identyfikator dla bieżącego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="739ba-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="739ba-108">[in] Kombinacji [validatorflags —](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości, wskazujący rodzaj sprawdzania poprawności, która powinna być wykonywana.</span><span class="sxs-lookup"><span data-stu-id="739ba-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="739ba-109">[in] Maksymalna liczba błędów, aby umożliwić przed zakończeniem weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="739ba-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="739ba-110">[in] Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="739ba-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="739ba-111">[in] Nazwa pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="739ba-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="739ba-112">[in] Wskaźnik do buforu plików.</span><span class="sxs-lookup"><span data-stu-id="739ba-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="739ba-113">[in] Rozmiar w bajtach, plików, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="739ba-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="739ba-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="739ba-114">Return Value</span></span>  
  
|<span data-ttu-id="739ba-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="739ba-115">HRESULT</span></span>|<span data-ttu-id="739ba-116">Opis</span><span class="sxs-lookup"><span data-stu-id="739ba-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="739ba-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="739ba-117">S_OK</span></span>|<span data-ttu-id="739ba-118">`Validate` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="739ba-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="739ba-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="739ba-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="739ba-120">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="739ba-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="739ba-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="739ba-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="739ba-122">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="739ba-122">The call timed out.</span></span>|  
|<span data-ttu-id="739ba-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="739ba-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="739ba-124">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="739ba-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="739ba-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="739ba-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="739ba-126">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="739ba-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="739ba-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="739ba-127">E_FAIL</span></span>|<span data-ttu-id="739ba-128">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="739ba-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="739ba-129">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="739ba-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="739ba-130">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="739ba-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="739ba-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="739ba-131">Requirements</span></span>  
 <span data-ttu-id="739ba-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="739ba-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="739ba-133">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="739ba-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="739ba-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="739ba-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="739ba-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="739ba-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739ba-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="739ba-136">See also</span></span>
- [<span data-ttu-id="739ba-137">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="739ba-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
