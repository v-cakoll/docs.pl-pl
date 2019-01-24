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
ms.openlocfilehash: bc3f9e8c581bc95bea8cfeb549177966eae22a43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584496"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="21825-102">IApartmentCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="21825-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="21825-103">Udostępnia metody do tworzenia wywołań zwrotnych w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="21825-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="21825-104">*Apartamentu* to logiczny kontener, w ramach procesu dla obiektów, które mają takie same wymagania dotyczące dostępu do wątku.</span><span class="sxs-lookup"><span data-stu-id="21825-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21825-105">Metody</span><span class="sxs-lookup"><span data-stu-id="21825-105">Methods</span></span>  
  
|<span data-ttu-id="21825-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="21825-106">Method</span></span>|<span data-ttu-id="21825-107">Opis</span><span class="sxs-lookup"><span data-stu-id="21825-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21825-108">DoCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="21825-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="21825-109">Wykonuje określoną funkcję w ramach typu apartment.</span><span class="sxs-lookup"><span data-stu-id="21825-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21825-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21825-110">Requirements</span></span>  
 <span data-ttu-id="21825-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21825-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21825-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21825-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21825-113">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21825-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21825-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21825-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21825-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21825-115">See also</span></span>
- [<span data-ttu-id="21825-116">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="21825-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
