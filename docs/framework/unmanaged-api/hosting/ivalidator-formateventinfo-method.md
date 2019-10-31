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
ms.openlocfilehash: 9b3a6bab8672f3ef3fca5f89c60b03a43477cce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123297"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="d6633-102">IValidator::FormatEventInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6633-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="d6633-103">Pobiera komunikat o błędzie odpowiadający określonemu błędowi walidacji.</span><span class="sxs-lookup"><span data-stu-id="d6633-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6633-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6633-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6633-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6633-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="d6633-106">podczas Wartość HRESULT, która została przeniesiona do procedury obsługi błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="d6633-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="d6633-107">podczas Wystąpienie `VEContext`, które zawiera informacje kontekstu dotyczące błędu walidacji.</span><span class="sxs-lookup"><span data-stu-id="d6633-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="d6633-108">[in. out] Ciąg, który zawiera zwracany komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="d6633-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="d6633-109">podczas Maksymalna długość komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="d6633-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="d6633-110">podczas Bezpieczna tablica zawierająca dodatkowe parametry opisujące błąd.</span><span class="sxs-lookup"><span data-stu-id="d6633-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6633-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6633-111">Requirements</span></span>  
 <span data-ttu-id="d6633-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6633-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6633-113">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="d6633-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="d6633-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6633-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6633-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6633-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
