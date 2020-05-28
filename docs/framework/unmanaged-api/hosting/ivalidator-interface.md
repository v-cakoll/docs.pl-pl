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
ms.openlocfilehash: d8e5ab607f9310341ded482b35f02f3845926328
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008563"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="a7417-102">IValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7417-102">IValidator Interface</span></span>
<span data-ttu-id="a7417-103">Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="a7417-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7417-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a7417-104">Methods</span></span>  
  
|<span data-ttu-id="a7417-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a7417-105">Method</span></span>|<span data-ttu-id="a7417-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a7417-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a7417-107">Walidacja</span><span class="sxs-lookup"><span data-stu-id="a7417-107">Validate</span></span>|<span data-ttu-id="a7417-108">Sprawdza poprawność określonego pliku PE lub języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="a7417-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="a7417-109">FormatEventInfo —</span><span class="sxs-lookup"><span data-stu-id="a7417-109">FormatEventInfo</span></span>|<span data-ttu-id="a7417-110">Pobiera komunikat o błędzie odpowiadający określonemu błędowi walidacji.</span><span class="sxs-lookup"><span data-stu-id="a7417-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7417-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7417-111">Requirements</span></span>  
 <span data-ttu-id="a7417-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7417-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7417-113">**Nagłówek:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="a7417-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a7417-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a7417-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7417-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7417-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7417-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7417-116">See also</span></span>

- [<span data-ttu-id="a7417-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a7417-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="a7417-118">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="a7417-118">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
