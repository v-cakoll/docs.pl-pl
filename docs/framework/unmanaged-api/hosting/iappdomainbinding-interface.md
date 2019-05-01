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
ms.openlocfilehash: e2c3a3057003d0035bfcb096a94c84d610e3056f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985516"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="3c88c-102">IAppDomainBinding — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3c88c-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="3c88c-103">Dostarcza metodę, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), by powiadomić aplikację hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c88c-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c88c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3c88c-104">Methods</span></span>  
  
|<span data-ttu-id="3c88c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c88c-105">Method</span></span>|<span data-ttu-id="3c88c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3c88c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c88c-107">OnAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="3c88c-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="3c88c-108">Metoda wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) w celu powiadomienia hosta, że utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3c88c-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c88c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c88c-109">Requirements</span></span>  
 <span data-ttu-id="3c88c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c88c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c88c-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c88c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c88c-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c88c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c88c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c88c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c88c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c88c-114">See also</span></span>

- [<span data-ttu-id="3c88c-115">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3c88c-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
