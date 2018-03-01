---
title: "EClrUnhandledException — Wyliczenie"
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
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8fcc9254499724d94153c445943fdaf78d12a10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="7ae19-102">EClrUnhandledException — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7ae19-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="7ae19-103">W tym artykule opisano dostępne opcje zarządzania wyjątki, które są nieobsługiwane w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7ae19-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ae19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ae19-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="7ae19-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7ae19-105">Members</span></span>  
  
|<span data-ttu-id="7ae19-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7ae19-106">Member</span></span>|<span data-ttu-id="7ae19-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7ae19-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="7ae19-108">Określa, czy wystąpi zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="7ae19-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="7ae19-109">Proces będzie działo.</span><span class="sxs-lookup"><span data-stu-id="7ae19-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="7ae19-110">Określa, że środowisko uruchomieniowe języka wspólnego (CLR) ignoruje nieobsługiwanych wyjątków i umożliwia hosta ustalić dalszych działań.</span><span class="sxs-lookup"><span data-stu-id="7ae19-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ae19-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ae19-111">Remarks</span></span>  
 <span data-ttu-id="7ae19-112">Aby określić, że przypominają wcześniejszych wersji środowiska CLR, użyj `eHostDeterminedPolicy` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7ae19-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ae19-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ae19-113">Requirements</span></span>  
 <span data-ttu-id="7ae19-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ae19-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ae19-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ae19-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ae19-116">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ae19-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ae19-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ae19-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae19-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ae19-118">See Also</span></span>  
 [<span data-ttu-id="7ae19-119">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7ae19-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="7ae19-120">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7ae19-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="7ae19-121">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ae19-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="7ae19-122">SetUnhandledExceptionPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="7ae19-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="7ae19-123">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ae19-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="7ae19-124">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7ae19-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
