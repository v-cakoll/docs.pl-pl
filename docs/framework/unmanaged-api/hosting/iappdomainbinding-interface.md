---
title: "IAppDomainBinding — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainBinding
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainBinding
helpviewer_keywords: IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a6f26c8337f89d829f42e00a9e5e79731a15156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="b2792-102">IAppDomainBinding — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b2792-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="b2792-103">Udostępnia metody, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), aby powiadomić aplikacji hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2792-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2792-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2792-104">Methods</span></span>  
  
|<span data-ttu-id="b2792-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2792-105">Method</span></span>|<span data-ttu-id="b2792-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b2792-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2792-107">OnAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="b2792-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="b2792-108">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby powiadomić hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2792-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2792-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2792-109">Requirements</span></span>  
 <span data-ttu-id="b2792-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2792-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2792-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2792-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2792-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2792-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2792-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2792-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2792-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2792-114">See Also</span></span>  
 [<span data-ttu-id="b2792-115">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b2792-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
