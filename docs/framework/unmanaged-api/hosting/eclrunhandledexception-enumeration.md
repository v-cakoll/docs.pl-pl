---
title: "EClrUnhandledException — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrUnhandledException
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrUnhandledException
helpviewer_keywords: EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67787072779e0cb22a339c2d13c972ba36f3ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="c8680-102">EClrUnhandledException — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8680-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="c8680-103">W tym artykule opisano dostępne opcje zarządzania wyjątki, które są nieobsługiwane w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c8680-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8680-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8680-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="c8680-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c8680-105">Members</span></span>  
  
|<span data-ttu-id="c8680-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c8680-106">Member</span></span>|<span data-ttu-id="c8680-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c8680-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="c8680-108">Określa, czy wystąpi zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="c8680-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="c8680-109">Proces będzie działo.</span><span class="sxs-lookup"><span data-stu-id="c8680-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="c8680-110">Określa, że środowisko uruchomieniowe języka wspólnego (CLR) ignoruje nieobsługiwanych wyjątków i umożliwia hosta ustalić dalszych działań.</span><span class="sxs-lookup"><span data-stu-id="c8680-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8680-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8680-111">Remarks</span></span>  
 <span data-ttu-id="c8680-112">Aby określić, że przypominają wcześniejszych wersji środowiska CLR, użyj `eHostDeterminedPolicy` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c8680-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8680-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8680-113">Requirements</span></span>  
 <span data-ttu-id="c8680-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8680-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8680-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8680-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8680-116">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8680-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8680-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8680-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8680-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8680-118">See Also</span></span>  
 [<span data-ttu-id="c8680-119">EClrFailure — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8680-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="c8680-120">EClrOperation — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c8680-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="c8680-121">ICLRPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="c8680-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="c8680-122">SetUnhandledExceptionPolicy — metoda</span><span class="sxs-lookup"><span data-stu-id="c8680-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="c8680-123">IHostPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="c8680-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="c8680-124">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c8680-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
