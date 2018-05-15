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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e79a69bf71aee035fb1f9a0178879d7c19e62b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ivalidator-interface"></a><span data-ttu-id="13e17-102">IValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="13e17-102">IValidator Interface</span></span>
<span data-ttu-id="13e17-103">Udostępnia metody dla sprawdzanie poprawności przenośne obrazy wykonywalne (PE) i raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="13e17-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13e17-104">Metody</span><span class="sxs-lookup"><span data-stu-id="13e17-104">Methods</span></span>  
  
|<span data-ttu-id="13e17-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="13e17-105">Method</span></span>|<span data-ttu-id="13e17-106">Opis</span><span class="sxs-lookup"><span data-stu-id="13e17-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="13e17-107">Sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="13e17-107">Validate</span></span>|<span data-ttu-id="13e17-108">Weryfikuje określony plik języka pośredniego (MSIL) PE lub firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="13e17-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="13e17-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="13e17-109">FormatEventInfo</span></span>|<span data-ttu-id="13e17-110">Pobiera odpowiadający błąd sprawdzania poprawności określony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="13e17-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13e17-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13e17-111">Requirements</span></span>  
 <span data-ttu-id="13e17-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e17-113">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="13e17-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="13e17-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13e17-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13e17-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e17-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e17-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13e17-116">See Also</span></span>  
 [<span data-ttu-id="13e17-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="13e17-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="13e17-118">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="13e17-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
