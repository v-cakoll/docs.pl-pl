---
title: CorRuntimeHost — Klasa coclass
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9b9b8a728932caa085bba1665dc97faf02be8fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="c59b6-102">CorRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="c59b6-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="c59b6-103">Udostępnia interfejsy związanych z zarządzaniem aplikacjami, które są wykonywane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c59b6-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c59b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c59b6-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="c59b6-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c59b6-105">Interfaces</span></span>  
  
|<span data-ttu-id="c59b6-106">Interface</span><span class="sxs-lookup"><span data-stu-id="c59b6-106">Interface</span></span>|<span data-ttu-id="c59b6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c59b6-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c59b6-108">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="c59b6-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="c59b6-109">Udostępnia metody konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c59b6-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="c59b6-110">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="c59b6-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="c59b6-111">Udostępnia metody umożliwiające hosta go uruchamiać i zatrzymywać środowisko uruchomieniowe języka wspólnego jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkie domeny uruchomionych w procesie.</span><span class="sxs-lookup"><span data-stu-id="c59b6-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="c59b6-112">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c59b6-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="c59b6-113">Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="c59b6-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="c59b6-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="c59b6-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="c59b6-115">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c59b6-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="c59b6-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="c59b6-116">"IValidator"</span></span>|<span data-ttu-id="c59b6-117">Udostępnia metody do weryfikacji przenośnych obrazy wykonywalne i szczegółowe raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="c59b6-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c59b6-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c59b6-118">Requirements</span></span>  
 <span data-ttu-id="c59b6-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c59b6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c59b6-120">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="c59b6-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c59b6-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c59b6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c59b6-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c59b6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c59b6-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c59b6-123">See Also</span></span>  
 [<span data-ttu-id="c59b6-124">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="c59b6-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
