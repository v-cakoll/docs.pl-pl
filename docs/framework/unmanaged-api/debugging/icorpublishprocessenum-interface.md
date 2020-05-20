---
title: ICorPublishProcessEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421075"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="3b437-102">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3b437-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="3b437-103">Podklasa interfejsu [ICorPublishEnum](icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3b437-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b437-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3b437-104">Methods</span></span>  
  
|<span data-ttu-id="3b437-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b437-105">Method</span></span>|<span data-ttu-id="3b437-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3b437-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b437-107">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b437-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="3b437-108">Pobiera określoną liczbę `ICorPublishProcess` wystąpień z kolekcji, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="3b437-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b437-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b437-109">Remarks</span></span>  
 <span data-ttu-id="3b437-110">`ICorPublishProcessEnum`Interfejs implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3b437-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="3b437-111">`ICorPublishProcessEnum`Wystąpienie jest tworzone przez metodę [ICorPublish:: EnumProcesses —](icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3b437-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="3b437-112">Przechodzenie kolekcji `ICorPublishProcess` obiektów jest oparte na kryteriach filtrowania określonych w momencie `ICorPublishProcessEnum` utworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3b437-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b437-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b437-113">Requirements</span></span>  
 <span data-ttu-id="3b437-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b437-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b437-115">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3b437-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3b437-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3b437-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b437-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b437-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b437-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b437-118">See also</span></span>

- [<span data-ttu-id="3b437-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3b437-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3b437-120">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="3b437-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
