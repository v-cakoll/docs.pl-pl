---
title: IAppDomainBinding — Interfejs
ms.date: 03/30/2017
api_name:
- IAppDomainBinding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainBinding
helpviewer_keywords:
- IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4be027238d676d78a3ec29e4f2696f765291f29b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504434"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="382d9-102">IAppDomainBinding — Interfejs</span><span class="sxs-lookup"><span data-stu-id="382d9-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="382d9-103">Dostarcza metodę, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), by powiadomić aplikację hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="382d9-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="382d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="382d9-104">Methods</span></span>  
  
|<span data-ttu-id="382d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="382d9-105">Method</span></span>|<span data-ttu-id="382d9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="382d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="382d9-107">OnAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="382d9-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="382d9-108">Metoda wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) w celu powiadomienia hosta, że utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="382d9-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="382d9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="382d9-109">Requirements</span></span>  
 <span data-ttu-id="382d9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="382d9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="382d9-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="382d9-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="382d9-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="382d9-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="382d9-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="382d9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382d9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="382d9-114">See also</span></span>
- [<span data-ttu-id="382d9-115">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="382d9-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
