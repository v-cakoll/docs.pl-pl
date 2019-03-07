---
title: IValidator::Validate — Metoda
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c362b41d842fb9d35cc7ae9293e2e305b2af281
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500437"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="1cfa7-102">IValidator::Validate — Metoda</span><span class="sxs-lookup"><span data-stu-id="1cfa7-102">IValidator::Validate Method</span></span>
<span data-ttu-id="1cfa7-103">Sprawdza poprawność określonego pliku wykonalnego (PE) lub pliku języka intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cfa7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cfa7-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cfa7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cfa7-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="1cfa7-106">[in] Wskaźnik do `IVEHandler` wystąpienia, która obsługuje błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1cfa7-107">[in] Wskaźnik do domeny aplikacji, w którym jest on ładowany.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="1cfa7-108">[in] Bitowa kombinacja [validatorflags —](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości, wskazujący operacji sprawdzania poprawności, które powinny być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="1cfa7-109">[in] Maksymalna liczba błędów, aby umożliwić przed zakończeniem weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="1cfa7-110">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1cfa7-111">[in] Ciąg, który określa nazwę pliku, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="1cfa7-112">[in] Wskaźnik do bufora pamięci, w którym jest przechowywany plik.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="1cfa7-113">[in] Rozmiar w bajtach, plików, który ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="1cfa7-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cfa7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1cfa7-114">Requirements</span></span>  
 <span data-ttu-id="1cfa7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cfa7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cfa7-116">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="1cfa7-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="1cfa7-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1cfa7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cfa7-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cfa7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cfa7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cfa7-119">See also</span></span>

