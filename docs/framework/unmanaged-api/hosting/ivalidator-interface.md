---
title: "IValidator — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator
api_location: mscoree.dll
api_type: COM
f1_keywords: IValidator
helpviewer_keywords: IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d88bfa0a3e71f34a7439e97f4347a06aa2c4058
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ivalidator-interface"></a><span data-ttu-id="3f70f-102">IValidator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f70f-102">IValidator Interface</span></span>
<span data-ttu-id="3f70f-103">Udostępnia metody dla sprawdzanie poprawności przenośne obrazy wykonywalne (PE) i raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="3f70f-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f70f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3f70f-104">Methods</span></span>  
  
|<span data-ttu-id="3f70f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f70f-105">Method</span></span>|<span data-ttu-id="3f70f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3f70f-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3f70f-107">Sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="3f70f-107">Validate</span></span>|<span data-ttu-id="3f70f-108">Weryfikuje określony plik języka pośredniego (MSIL) PE lub firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3f70f-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="3f70f-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="3f70f-109">FormatEventInfo</span></span>|<span data-ttu-id="3f70f-110">Pobiera odpowiadający błąd sprawdzania poprawności określony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="3f70f-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f70f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f70f-111">Requirements</span></span>  
 <span data-ttu-id="3f70f-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f70f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f70f-113">**Nagłówek:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="3f70f-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="3f70f-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f70f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f70f-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f70f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f70f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f70f-116">See Also</span></span>  
 [<span data-ttu-id="3f70f-117">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="3f70f-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="3f70f-118">Corruntimehost — klasa Coclass</span><span class="sxs-lookup"><span data-stu-id="3f70f-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
