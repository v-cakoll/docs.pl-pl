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
ms.openlocfilehash: 6e40f08a3dae6f17617e97e07a23b9d7eb611083
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558634"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="59eda-102">CLRRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="59eda-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="59eda-103">Zawiera interfejsy zarządzania wykonywania kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="59eda-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59eda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59eda-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="59eda-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="59eda-105">Interfaces</span></span>  
  
|<span data-ttu-id="59eda-106">Interface</span><span class="sxs-lookup"><span data-stu-id="59eda-106">Interface</span></span>|<span data-ttu-id="59eda-107">Opis</span><span class="sxs-lookup"><span data-stu-id="59eda-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="59eda-108">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="59eda-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="59eda-109">Udostępnia metody do kontroli wykonania aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="59eda-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="59eda-110">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="59eda-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="59eda-111">Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów oraz szczegółowe raporty błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="59eda-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59eda-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59eda-112">Requirements</span></span>  
 <span data-ttu-id="59eda-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59eda-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59eda-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="59eda-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="59eda-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59eda-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59eda-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59eda-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59eda-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59eda-117">See also</span></span>
- [<span data-ttu-id="59eda-118">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="59eda-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
