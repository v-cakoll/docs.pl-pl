---
title: "CLRRuntimeHost — Klasa coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18e4518a2e321609a8add06c399ed9588748d1ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="b12e8-102">CLRRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="b12e8-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="b12e8-103">Zawiera interfejsy zarządzania wykonywanie kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b12e8-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b12e8-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="b12e8-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b12e8-105">Interfaces</span></span>  
  
|<span data-ttu-id="b12e8-106">Interface</span><span class="sxs-lookup"><span data-stu-id="b12e8-106">Interface</span></span>|<span data-ttu-id="b12e8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b12e8-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b12e8-108">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="b12e8-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="b12e8-109">Udostępnia metody do kontroli wykonania aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b12e8-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="b12e8-110">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="b12e8-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="b12e8-111">Udostępnia metody weryfikacji przenośnych obrazy wykonywalne oraz szczegółowe raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="b12e8-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b12e8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b12e8-112">Requirements</span></span>  
 <span data-ttu-id="b12e8-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12e8-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="b12e8-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b12e8-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b12e8-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b12e8-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12e8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b12e8-117">See Also</span></span>  
 [<span data-ttu-id="b12e8-118">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="b12e8-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
