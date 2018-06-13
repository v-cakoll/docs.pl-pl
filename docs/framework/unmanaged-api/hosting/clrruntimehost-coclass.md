---
title: CLRRuntimeHost — Klasa coclass
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59fed7519402b4c3c1b2405ea99f8ba484781e95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430746"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="37401-102">CLRRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="37401-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="37401-103">Zawiera interfejsy zarządzania wykonywanie kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="37401-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37401-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37401-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="37401-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="37401-105">Interfaces</span></span>  
  
|<span data-ttu-id="37401-106">Interface</span><span class="sxs-lookup"><span data-stu-id="37401-106">Interface</span></span>|<span data-ttu-id="37401-107">Opis</span><span class="sxs-lookup"><span data-stu-id="37401-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="37401-108">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="37401-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="37401-109">Udostępnia metody do kontroli wykonania aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="37401-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="37401-110">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="37401-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="37401-111">Udostępnia metody weryfikacji przenośnych obrazy wykonywalne oraz szczegółowe raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="37401-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37401-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37401-112">Requirements</span></span>  
 <span data-ttu-id="37401-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37401-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37401-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="37401-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="37401-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37401-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37401-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37401-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37401-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37401-117">See Also</span></span>  
 [<span data-ttu-id="37401-118">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="37401-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
