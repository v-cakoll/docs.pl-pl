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
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178061"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="646a0-102">ICLRValidator::Validate — Metoda</span><span class="sxs-lookup"><span data-stu-id="646a0-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="646a0-103">Sprawdza poprawność przenośnego pliku wykonywalnego (PE) lub języka pośredniego firmy Microsoft (MSIL) w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="646a0-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="646a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="646a0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="646a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="646a0-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="646a0-106">[w] Wskaźnik do `IVEHandler` wystąpienia, który obsługuje błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="646a0-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="646a0-107">[w] Identyfikator bieżącego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="646a0-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="646a0-108">[w] Kombinacja [Wartości ValidatorFlags,](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wskazując rodzaj sprawdzania poprawności, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="646a0-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="646a0-109">[w] Maksymalna liczba błędów, które należy zezwolić przed zamknięciem sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="646a0-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="646a0-110">[w] Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="646a0-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="646a0-111">[w] Nazwa pliku, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="646a0-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="646a0-112">[w] Wskaźnik do buforu plików.</span><span class="sxs-lookup"><span data-stu-id="646a0-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="646a0-113">[w] Rozmiar w bajtach pliku, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="646a0-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="646a0-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="646a0-114">Return Value</span></span>  
  
|<span data-ttu-id="646a0-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="646a0-115">HRESULT</span></span>|<span data-ttu-id="646a0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="646a0-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="646a0-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="646a0-117">S_OK</span></span>|<span data-ttu-id="646a0-118">`Validate`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="646a0-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="646a0-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="646a0-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="646a0-120">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="646a0-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="646a0-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="646a0-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="646a0-122">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="646a0-122">The call timed out.</span></span>|  
|<span data-ttu-id="646a0-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="646a0-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="646a0-124">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="646a0-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="646a0-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="646a0-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="646a0-126">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="646a0-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="646a0-127">E_fail</span><span class="sxs-lookup"><span data-stu-id="646a0-127">E_FAIL</span></span>|<span data-ttu-id="646a0-128">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="646a0-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="646a0-129">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="646a0-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="646a0-130">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="646a0-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="646a0-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="646a0-131">Requirements</span></span>  
 <span data-ttu-id="646a0-132">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="646a0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="646a0-133">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="646a0-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="646a0-134">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="646a0-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="646a0-135">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="646a0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646a0-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="646a0-136">See also</span></span>

- [<span data-ttu-id="646a0-137">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="646a0-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
