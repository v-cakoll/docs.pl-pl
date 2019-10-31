---
title: IValidator — Interfejs
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
ms.openlocfilehash: 1a732e59d539c330f91e8665e81dc4771b40e2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123283"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="f3b42-102">IValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f3b42-102">IValidator Interface</span></span>
<span data-ttu-id="f3b42-103">Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="f3b42-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3b42-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f3b42-104">Methods</span></span>  
  
|<span data-ttu-id="f3b42-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f3b42-105">Method</span></span>|<span data-ttu-id="f3b42-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f3b42-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f3b42-107">legalizacj</span><span class="sxs-lookup"><span data-stu-id="f3b42-107">Validate</span></span>|<span data-ttu-id="f3b42-108">Sprawdza poprawność określonego pliku PE lub języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="f3b42-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="f3b42-109">FormatEventInfo —</span><span class="sxs-lookup"><span data-stu-id="f3b42-109">FormatEventInfo</span></span>|<span data-ttu-id="f3b42-110">Pobiera komunikat o błędzie odpowiadający określonemu błędowi walidacji.</span><span class="sxs-lookup"><span data-stu-id="f3b42-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3b42-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3b42-111">Requirements</span></span>  
 <span data-ttu-id="f3b42-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3b42-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3b42-113">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="f3b42-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="f3b42-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3b42-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3b42-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3b42-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b42-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3b42-116">See also</span></span>

- [<span data-ttu-id="f3b42-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f3b42-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f3b42-118">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="f3b42-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
