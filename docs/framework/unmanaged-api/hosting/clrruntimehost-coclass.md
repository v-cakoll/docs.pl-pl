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
ms.openlocfilehash: 841b05ca1037d82046820554878d883f94687d34
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779150"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="11079-102">CLRRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="11079-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="11079-103">Zawiera interfejsy zarządzania wykonywania kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11079-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11079-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11079-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="11079-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="11079-105">Interfaces</span></span>  
  
|<span data-ttu-id="11079-106">Interface</span><span class="sxs-lookup"><span data-stu-id="11079-106">Interface</span></span>|<span data-ttu-id="11079-107">Opis</span><span class="sxs-lookup"><span data-stu-id="11079-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="11079-108">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="11079-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="11079-109">Udostępnia metody do kontroli wykonania aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11079-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="11079-110">ICLRValidator, interfejs</span><span class="sxs-lookup"><span data-stu-id="11079-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="11079-111">Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów oraz szczegółowe raporty błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="11079-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11079-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11079-112">Requirements</span></span>  
 <span data-ttu-id="11079-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11079-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11079-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="11079-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="11079-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11079-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11079-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11079-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11079-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11079-117">See also</span></span>

- [<span data-ttu-id="11079-118">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="11079-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
