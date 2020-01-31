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
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790508"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="39701-102">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="39701-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="39701-103">Podklasa interfejsu [ICorPublishEnum](icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="39701-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39701-104">Metody</span><span class="sxs-lookup"><span data-stu-id="39701-104">Methods</span></span>  
  
|<span data-ttu-id="39701-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="39701-105">Method</span></span>|<span data-ttu-id="39701-106">Opis</span><span class="sxs-lookup"><span data-stu-id="39701-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39701-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="39701-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="39701-108">Pobiera określoną liczbę wystąpień `ICorPublishProcess` z kolekcji, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="39701-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39701-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39701-109">Remarks</span></span>  
 <span data-ttu-id="39701-110">Interfejs `ICorPublishProcessEnum` implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="39701-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="39701-111">Wystąpienie `ICorPublishProcessEnum` jest tworzone przez metodę [ICorPublish:: EnumProcesses —](icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="39701-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="39701-112">Przechodzenie kolekcji obiektów `ICorPublishProcess` jest oparte na kryteriach filtrowania określonych w momencie utworzenia wystąpienia `ICorPublishProcessEnum`.</span><span class="sxs-lookup"><span data-stu-id="39701-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39701-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39701-113">Requirements</span></span>  
 <span data-ttu-id="39701-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39701-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39701-115">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="39701-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="39701-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="39701-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39701-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39701-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39701-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39701-118">See also</span></span>

- [<span data-ttu-id="39701-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="39701-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="39701-120">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="39701-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
