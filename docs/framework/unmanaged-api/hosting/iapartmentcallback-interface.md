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
ms.openlocfilehash: 4424509c16dd1d9f83db117ae7343fa03995297e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126914"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="f038b-102">IApartmentCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f038b-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="f038b-103">Zapewnia metody tworzenia wywołań zwrotnych w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="f038b-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="f038b-104">*Apartament* jest kontenerem logicznym w ramach procesu dla obiektów, które mają takie same wymagania dotyczące dostępu do wątków.</span><span class="sxs-lookup"><span data-stu-id="f038b-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f038b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f038b-105">Methods</span></span>  
  
|<span data-ttu-id="f038b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f038b-106">Method</span></span>|<span data-ttu-id="f038b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f038b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f038b-108">DoCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="f038b-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="f038b-109">Wykonuje określoną funkcję w obrębie apartamentu.</span><span class="sxs-lookup"><span data-stu-id="f038b-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f038b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f038b-110">Requirements</span></span>  
 <span data-ttu-id="f038b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f038b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f038b-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f038b-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f038b-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f038b-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f038b-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f038b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f038b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f038b-115">See also</span></span>

- [<span data-ttu-id="f038b-116">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f038b-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
