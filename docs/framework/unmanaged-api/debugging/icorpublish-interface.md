---
title: ICorPublish — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 1bd2f537cfa6a27c24ba91ea7caa29dc9e71a74e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396322"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="9cdee-102">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9cdee-102">ICorPublish Interface</span></span>
<span data-ttu-id="9cdee-103">Służy jako ogólny interfejs publikowania informacji o procesach i informacjach o domenach aplikacji w tych procesach.</span><span class="sxs-lookup"><span data-stu-id="9cdee-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9cdee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9cdee-104">Methods</span></span>  
  
|<span data-ttu-id="9cdee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9cdee-105">Method</span></span>|<span data-ttu-id="9cdee-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9cdee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9cdee-107">EnumProcesses, metoda</span><span class="sxs-lookup"><span data-stu-id="9cdee-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="9cdee-108">Pobiera wystąpienie [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) , które zawiera zarządzane procesy uruchomione na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9cdee-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="9cdee-109">GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cdee-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="9cdee-110">Pobiera wystąpienie [ICorPublishProcess](icorpublishprocess-interface.md) , które reprezentuje proces o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="9cdee-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cdee-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cdee-111">Requirements</span></span>  
 <span data-ttu-id="9cdee-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cdee-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cdee-113">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="9cdee-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9cdee-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9cdee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cdee-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cdee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdee-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cdee-116">See also</span></span>

- [<span data-ttu-id="9cdee-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9cdee-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9cdee-118">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="9cdee-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
