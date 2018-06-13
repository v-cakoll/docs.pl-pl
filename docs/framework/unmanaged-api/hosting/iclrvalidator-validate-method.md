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
ms.openlocfilehash: b2ad9ef473a498804e5b3ac0469b5b68697c49f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439176"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="74629-102">ICLRValidator::Validate — Metoda</span><span class="sxs-lookup"><span data-stu-id="74629-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="74629-103">Weryfikuje przenośny plik wykonywalny (PE) lub język pośredni firmy Microsoft (MSIL) w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="74629-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74629-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74629-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="74629-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74629-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="74629-106">[in] Wskaźnik do `IVEHandler` wystąpienie, które obsługuje błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="74629-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="74629-107">[in] Identyfikator bieżącego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="74629-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="74629-108">[in] Kombinację [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości i wskazujący rodzaj weryfikacji, które powinno być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="74629-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="74629-109">[in] Maksymalna liczba błędów umożliwia przed zakończeniem sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="74629-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="74629-110">[in] Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="74629-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="74629-111">[in] Nazwa pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="74629-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="74629-112">[in] Wskaźnik do pliku buforu.</span><span class="sxs-lookup"><span data-stu-id="74629-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="74629-113">[in] Rozmiar w bajtach, pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="74629-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74629-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="74629-114">Return Value</span></span>  
  
|<span data-ttu-id="74629-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74629-115">HRESULT</span></span>|<span data-ttu-id="74629-116">Opis</span><span class="sxs-lookup"><span data-stu-id="74629-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74629-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="74629-117">S_OK</span></span>|<span data-ttu-id="74629-118">`Validate` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="74629-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="74629-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74629-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74629-120">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="74629-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74629-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74629-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74629-122">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="74629-122">The call timed out.</span></span>|  
|<span data-ttu-id="74629-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74629-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74629-124">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="74629-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74629-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74629-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74629-126">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="74629-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74629-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74629-127">E_FAIL</span></span>|<span data-ttu-id="74629-128">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="74629-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74629-129">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="74629-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74629-130">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74629-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74629-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74629-131">Requirements</span></span>  
 <span data-ttu-id="74629-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74629-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74629-133">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="74629-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="74629-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74629-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74629-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74629-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74629-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74629-136">See Also</span></span>  
 [<span data-ttu-id="74629-137">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="74629-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
