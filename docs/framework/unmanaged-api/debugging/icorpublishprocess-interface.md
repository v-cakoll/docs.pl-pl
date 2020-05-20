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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421088"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="acdf5-102">ICorPublishProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="acdf5-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="acdf5-103">Dostarcza metody, które mają dostęp do informacji o procesie.</span><span class="sxs-lookup"><span data-stu-id="acdf5-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acdf5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="acdf5-104">Methods</span></span>  
  
|<span data-ttu-id="acdf5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="acdf5-105">Method</span></span>|<span data-ttu-id="acdf5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="acdf5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acdf5-107">EnumAppDomains, metoda</span><span class="sxs-lookup"><span data-stu-id="acdf5-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="acdf5-108">Pobiera wystąpienie [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) , które zawiera domeny aplikacji w procesie, do którego się odwołuje `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="acdf5-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="acdf5-109">GetDisplayName — Metoda</span><span class="sxs-lookup"><span data-stu-id="acdf5-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="acdf5-110">Pobiera pełną ścieżkę pliku wykonywalnego dla procesu, do którego się odwołuje `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="acdf5-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="acdf5-111">GetProcessID, metoda</span><span class="sxs-lookup"><span data-stu-id="acdf5-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="acdf5-112">Pobiera identyfikator systemu operacyjnego dla procesu, do którego się odwołuje `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="acdf5-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="acdf5-113">IsManaged, metoda</span><span class="sxs-lookup"><span data-stu-id="acdf5-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="acdf5-114">Pobiera wartość wskazującą, czy proces, do którego się odwołuje, `ICorPublishProcess` jest znany jako uruchomiony kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="acdf5-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="acdf5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="acdf5-115">Requirements</span></span>  
 <span data-ttu-id="acdf5-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acdf5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acdf5-117">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="acdf5-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="acdf5-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="acdf5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acdf5-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acdf5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acdf5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acdf5-120">See also</span></span>

- [<span data-ttu-id="acdf5-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="acdf5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="acdf5-122">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="acdf5-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
