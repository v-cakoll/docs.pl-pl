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
ms.openlocfilehash: 164a8c15a501af44aabb95852400621f05bbe873
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762802"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="0fb55-102">ICLRValidator::FormatEventInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="0fb55-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="0fb55-103">Pobiera szczegółowy komunikat o określonym błędzie walidacji.</span><span class="sxs-lookup"><span data-stu-id="0fb55-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fb55-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fb55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fb55-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="0fb55-106">podczas Wartość HRESULT, która została przeniesiona do procedury obsługi błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="0fb55-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="0fb55-107">podczas `VEContext`Wystąpienie zawierające informacje o kontekście błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="0fb55-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="0fb55-108">[in. out] Przyjazny komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="0fb55-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="0fb55-109">podczas Maksymalna długość komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="0fb55-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="0fb55-110">podczas Bezpieczna tablica dodatkowych parametrów do użycia w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="0fb55-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fb55-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0fb55-111">Return Value</span></span>  
  
|<span data-ttu-id="0fb55-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fb55-112">HRESULT</span></span>|<span data-ttu-id="0fb55-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0fb55-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fb55-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0fb55-114">S_OK</span></span>|<span data-ttu-id="0fb55-115">`FormatEventInfo`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="0fb55-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="0fb55-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0fb55-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0fb55-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0fb55-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0fb55-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0fb55-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0fb55-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="0fb55-119">The call timed out.</span></span>|  
|<span data-ttu-id="0fb55-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fb55-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0fb55-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0fb55-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0fb55-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0fb55-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0fb55-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="0fb55-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0fb55-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0fb55-124">E_FAIL</span></span>|<span data-ttu-id="0fb55-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0fb55-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0fb55-126">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="0fb55-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0fb55-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0fb55-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fb55-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fb55-128">Requirements</span></span>  
 <span data-ttu-id="0fb55-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fb55-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fb55-130">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="0fb55-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="0fb55-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0fb55-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fb55-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fb55-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb55-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fb55-133">See also</span></span>

- [<span data-ttu-id="0fb55-134">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fb55-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="0fb55-135">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fb55-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
