---
title: IValidator::FormatEventInfo — Metoda
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: 0c60631b5e034bc46d74412440d35d526359d043
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008576"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="e69ec-102">IValidator::FormatEventInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="e69ec-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="e69ec-103">Pobiera komunikat o błędzie odpowiadający określonemu błędowi walidacji.</span><span class="sxs-lookup"><span data-stu-id="e69ec-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e69ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e69ec-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e69ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e69ec-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="e69ec-106">podczas Wartość HRESULT, która została przeniesiona do procedury obsługi błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="e69ec-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="e69ec-107">podczas `VEContext`Wystąpienie zawierające informacje kontekstu dotyczące błędu walidacji.</span><span class="sxs-lookup"><span data-stu-id="e69ec-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="e69ec-108">[in. out] Ciąg, który zawiera zwracany komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="e69ec-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="e69ec-109">podczas Maksymalna długość komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="e69ec-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="e69ec-110">podczas Bezpieczna tablica zawierająca dodatkowe parametry opisujące błąd.</span><span class="sxs-lookup"><span data-stu-id="e69ec-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e69ec-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e69ec-111">Requirements</span></span>  
 <span data-ttu-id="e69ec-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e69ec-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e69ec-113">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="e69ec-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e69ec-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e69ec-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e69ec-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e69ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
