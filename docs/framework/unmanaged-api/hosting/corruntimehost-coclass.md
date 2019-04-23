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
ms.openlocfilehash: 2143fc13db1757ac2fa8a9c5a43f104a0c519ca0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218566"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="e952a-102">CorRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="e952a-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="e952a-103">Zawiera interfejsy zarządzania aplikacji, które są wykonywane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e952a-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e952a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e952a-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="e952a-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e952a-105">Interfaces</span></span>  
  
|<span data-ttu-id="e952a-106">Interface</span><span class="sxs-lookup"><span data-stu-id="e952a-106">Interface</span></span>|<span data-ttu-id="e952a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e952a-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e952a-108">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="e952a-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="e952a-109">Udostępnia metody do konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e952a-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="e952a-110">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e952a-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="e952a-111">Udostępnia metody umożliwiające hosta do uruchamiania i zatrzymywania środowiska uruchomieniowego języka wspólnego jawnie, aby utworzyć i skonfigurować domeny aplikacji, dostęp do domyślnej domeny i wyliczyć wszystkich domen, uruchomiony w procesie.</span><span class="sxs-lookup"><span data-stu-id="e952a-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="e952a-112">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e952a-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="e952a-113">Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="e952a-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="e952a-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e952a-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="e952a-115">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektóre aspekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e952a-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="e952a-116">Ivalidator "—"</span><span class="sxs-lookup"><span data-stu-id="e952a-116">"IValidator"</span></span>|<span data-ttu-id="e952a-117">Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów i szczegółowe raporty błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="e952a-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e952a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e952a-118">Requirements</span></span>  
 <span data-ttu-id="e952a-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e952a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e952a-120">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="e952a-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e952a-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e952a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e952a-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e952a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e952a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e952a-123">See also</span></span>

- [<span data-ttu-id="e952a-124">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="e952a-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
