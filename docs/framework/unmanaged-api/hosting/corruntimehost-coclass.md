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
ms.openlocfilehash: fe378307ce2bda6e1a267e46433ead70a0e2299e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616525"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="f09a5-102">CorRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="f09a5-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="f09a5-103">Udostępnia interfejsy do zarządzania aplikacjami, które są wykonywane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f09a5-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f09a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f09a5-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="f09a5-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f09a5-105">Interfaces</span></span>  
  
|<span data-ttu-id="f09a5-106">Interfejs</span><span class="sxs-lookup"><span data-stu-id="f09a5-106">Interface</span></span>|<span data-ttu-id="f09a5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f09a5-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="f09a5-108">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="f09a5-108">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="f09a5-109">Zapewnia metody konfigurowania środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f09a5-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="f09a5-110">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f09a5-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="f09a5-111">Zapewnia metody umożliwiające uruchamianie hosta i zatrzymywanie jawnie środowiska uruchomieniowego języka wspólnego, tworzenie i Konfigurowanie domen aplikacji, dostęp do domeny domyślnej oraz wyliczanie wszystkich domen uruchomionych w procesie.</span><span class="sxs-lookup"><span data-stu-id="f09a5-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="f09a5-112">IDebuggerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f09a5-112">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="f09a5-113">Zapewnia metody uzyskiwania informacji o stanie usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="f09a5-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="f09a5-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f09a5-114">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="f09a5-115">Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f09a5-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="f09a5-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="f09a5-116">"IValidator"</span></span>|<span data-ttu-id="f09a5-117">Zapewnia metody weryfikacji przenośnych obrazów wykonywalnych i szczegółowe raportowanie błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="f09a5-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f09a5-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f09a5-118">Requirements</span></span>  
 <span data-ttu-id="f09a5-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f09a5-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f09a5-120">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="f09a5-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f09a5-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f09a5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f09a5-122">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f09a5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09a5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f09a5-123">See also</span></span>

- [<span data-ttu-id="f09a5-124">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="f09a5-124">Hosting Coclasses</span></span>](hosting-coclasses.md)
