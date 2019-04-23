---
title: ICorPublishProcess — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182965"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="5c60a-102">ICorPublishProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5c60a-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="5c60a-103">Udostępnia metody, uzyskujących dostęp do informacji wyświetlanych informacji na temat procesu.</span><span class="sxs-lookup"><span data-stu-id="5c60a-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c60a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5c60a-104">Methods</span></span>  
  
|<span data-ttu-id="5c60a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5c60a-105">Method</span></span>|<span data-ttu-id="5c60a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5c60a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c60a-107">EnumAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="5c60a-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="5c60a-108">Pobiera [icorpublishappdomainenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) wystąpienia, które zawiera domen aplikacji w procesie przywoływane przez to `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5c60a-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5c60a-109">GetDisplayName, metoda</span><span class="sxs-lookup"><span data-stu-id="5c60a-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="5c60a-110">Pobiera pełną ścieżkę pliku wykonywalnego procesu odwołuje się ten `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5c60a-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5c60a-111">GetProcessID, metoda</span><span class="sxs-lookup"><span data-stu-id="5c60a-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="5c60a-112">Pobiera identyfikator systemu operacyjnego dla procesu, który odwołuje się ten `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5c60a-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5c60a-113">IsManaged, metoda</span><span class="sxs-lookup"><span data-stu-id="5c60a-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="5c60a-114">Pobiera wartość wskazującą, czy proces odwołuje się ten `ICorPublishProcess` jest znany uruchomienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5c60a-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c60a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c60a-115">Requirements</span></span>  
 <span data-ttu-id="5c60a-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c60a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c60a-117">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5c60a-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5c60a-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c60a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c60a-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c60a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c60a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c60a-120">See also</span></span>

- [<span data-ttu-id="5c60a-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5c60a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5c60a-122">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="5c60a-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
