---
title: IApartmentCallback — Interfejs
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffa06fd42b5cfa09817bae9f0b3a3810e30f99c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430970"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="cf790-102">IApartmentCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cf790-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="cf790-103">Udostępnia metody do tworzenia wywołań zwrotnych w apartamencie.</span><span class="sxs-lookup"><span data-stu-id="cf790-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="cf790-104">*Apartamentu* jest kontenerem logicznym, w ramach procesu dla obiektów, które mają te same wymagania dostępu wątku.</span><span class="sxs-lookup"><span data-stu-id="cf790-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf790-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cf790-105">Methods</span></span>  
  
|<span data-ttu-id="cf790-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cf790-106">Method</span></span>|<span data-ttu-id="cf790-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cf790-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf790-108">DoCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="cf790-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="cf790-109">Wykonuje określoną funkcję w apartamencie.</span><span class="sxs-lookup"><span data-stu-id="cf790-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf790-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf790-110">Requirements</span></span>  
 <span data-ttu-id="cf790-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf790-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf790-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf790-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf790-113">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf790-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf790-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf790-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf790-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf790-115">See Also</span></span>  
 [<span data-ttu-id="cf790-116">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cf790-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
