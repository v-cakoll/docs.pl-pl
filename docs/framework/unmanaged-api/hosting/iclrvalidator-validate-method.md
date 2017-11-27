---
title: "ICLRValidator::Validate — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 50915201b6e57bd116b80f067f01b8862372bc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="85db8-102">ICLRValidator::Validate — Metoda</span><span class="sxs-lookup"><span data-stu-id="85db8-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="85db8-103">Weryfikuje przenośny plik wykonywalny (PE) lub język pośredni firmy Microsoft (MSIL) w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="85db8-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85db8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85db8-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="85db8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85db8-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="85db8-106">[in] Wskaźnik do `IVEHandler` wystąpienie, które obsługuje błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="85db8-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="85db8-107">[in] Identyfikator bieżącego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="85db8-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="85db8-108">[in] Kombinację [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości i wskazujący rodzaj weryfikacji, które powinno być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="85db8-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="85db8-109">[in] Maksymalna liczba błędów umożliwia przed zakończeniem sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="85db8-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="85db8-110">[in] Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="85db8-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="85db8-111">[in] Nazwa pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="85db8-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="85db8-112">[in] Wskaźnik do pliku buforu.</span><span class="sxs-lookup"><span data-stu-id="85db8-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="85db8-113">[in] Rozmiar w bajtach, pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="85db8-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85db8-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="85db8-114">Return Value</span></span>  
  
|<span data-ttu-id="85db8-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85db8-115">HRESULT</span></span>|<span data-ttu-id="85db8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="85db8-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85db8-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="85db8-117">S_OK</span></span>|<span data-ttu-id="85db8-118">`Validate`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="85db8-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="85db8-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85db8-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85db8-120">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="85db8-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85db8-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85db8-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85db8-122">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="85db8-122">The call timed out.</span></span>|  
|<span data-ttu-id="85db8-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85db8-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85db8-124">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="85db8-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85db8-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85db8-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85db8-126">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="85db8-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85db8-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85db8-127">E_FAIL</span></span>|<span data-ttu-id="85db8-128">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="85db8-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85db8-129">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="85db8-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85db8-130">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="85db8-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85db8-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85db8-131">Requirements</span></span>  
 <span data-ttu-id="85db8-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85db8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85db8-133">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="85db8-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="85db8-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85db8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85db8-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85db8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85db8-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85db8-136">See Also</span></span>  
 [<span data-ttu-id="85db8-137">ICLRValidator — interfejs</span><span class="sxs-lookup"><span data-stu-id="85db8-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
