---
title: "CorRuntimeHost — Klasa coclass"
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
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23bee1a79dfb54a696495fdb61a7ba9ba4b4c143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="b3b4d-102">CorRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="b3b4d-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="b3b4d-103">Udostępnia interfejsy związanych z zarządzaniem aplikacjami, które są wykonywane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b3b4d-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b4d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3b4d-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="b3b4d-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b3b4d-105">Interfaces</span></span>  
  
|<span data-ttu-id="b3b4d-106">Interface</span><span class="sxs-lookup"><span data-stu-id="b3b4d-106">Interface</span></span>|<span data-ttu-id="b3b4d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b3b4d-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b3b4d-108">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3b4d-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="b3b4d-109">Udostępnia metody konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b3b4d-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="b3b4d-110">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3b4d-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="b3b4d-111">Udostępnia metody umożliwiające hosta go uruchamiać i zatrzymywać środowisko uruchomieniowe języka wspólnego jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkie domeny uruchomionych w procesie.</span><span class="sxs-lookup"><span data-stu-id="b3b4d-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="b3b4d-112">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3b4d-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="b3b4d-113">Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3b4d-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="b3b4d-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3b4d-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="b3b4d-115">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b3b4d-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="b3b4d-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="b3b4d-116">"IValidator"</span></span>|<span data-ttu-id="b3b4d-117">Udostępnia metody do weryfikacji przenośnych obrazy wykonywalne i szczegółowe raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="b3b4d-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3b4d-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3b4d-118">Requirements</span></span>  
 <span data-ttu-id="b3b4d-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3b4d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b4d-120">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="b3b4d-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b3b4d-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3b4d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3b4d-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b4d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b4d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3b4d-123">See Also</span></span>  
 [<span data-ttu-id="b3b4d-124">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="b3b4d-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
