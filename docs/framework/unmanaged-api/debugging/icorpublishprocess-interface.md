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
ms.openlocfilehash: 04f6a088c5bbe96e3909ba600aa8ffab937abe2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140402"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="b91a9-102">ICorPublishProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b91a9-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="b91a9-103">Dostarcza metody, które mają dostęp do informacji o procesie.</span><span class="sxs-lookup"><span data-stu-id="b91a9-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b91a9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b91a9-104">Methods</span></span>  
  
|<span data-ttu-id="b91a9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b91a9-105">Method</span></span>|<span data-ttu-id="b91a9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b91a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b91a9-107">EnumAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="b91a9-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="b91a9-108">Pobiera wystąpienie [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) , które zawiera domeny aplikacji w procesie, do którego odwołuje się ten `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="b91a9-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b91a9-109">GetDisplayName, metoda</span><span class="sxs-lookup"><span data-stu-id="b91a9-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="b91a9-110">Pobiera pełną ścieżkę pliku wykonywalnego dla procesu, do którego odwołuje się ten `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="b91a9-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b91a9-111">GetProcessID, metoda</span><span class="sxs-lookup"><span data-stu-id="b91a9-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="b91a9-112">Pobiera identyfikator systemu operacyjnego dla procesu, do którego odwołuje się ten `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="b91a9-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b91a9-113">IsManaged, metoda</span><span class="sxs-lookup"><span data-stu-id="b91a9-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="b91a9-114">Pobiera wartość wskazującą, czy proces, do którego odwołuje się ten `ICorPublishProcess`, jest znany jako uruchomiony kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b91a9-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b91a9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b91a9-115">Requirements</span></span>  
 <span data-ttu-id="b91a9-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b91a9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91a9-117">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b91a9-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b91a9-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b91a9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b91a9-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91a9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91a9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b91a9-120">See also</span></span>

- [<span data-ttu-id="b91a9-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b91a9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b91a9-122">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="b91a9-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
