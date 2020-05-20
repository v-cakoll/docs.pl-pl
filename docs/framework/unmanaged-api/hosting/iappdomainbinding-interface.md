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
ms.openlocfilehash: c6f368f4288f8203067c1f9ff350ce0f3389f514
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617099"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="63350-102">IAppDomainBinding — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63350-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="63350-103">Zapewnia metodę, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania aplikacji hosta o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63350-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63350-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63350-104">Methods</span></span>  
  
|<span data-ttu-id="63350-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63350-105">Method</span></span>|<span data-ttu-id="63350-106">Opis</span><span class="sxs-lookup"><span data-stu-id="63350-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63350-107">OnAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="63350-107">OnAppDomain Method</span></span>](iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="63350-108">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania hosta o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63350-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63350-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63350-109">Requirements</span></span>  
 <span data-ttu-id="63350-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63350-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63350-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63350-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63350-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63350-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63350-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63350-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63350-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63350-114">See also</span></span>

- [<span data-ttu-id="63350-115">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="63350-115">Hosting Interfaces</span></span>](hosting-interfaces.md)
