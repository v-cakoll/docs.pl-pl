---
title: ICorPublish::EnumProcesses — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb4096b0ae083e0b6c0598ea18cc8b33c2fdfe3e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116298"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="690d4-102">ICorPublish::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="690d4-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="690d4-103">Pobiera moduł wyliczający dla zarządzanego procesów uruchomionych na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="690d4-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="690d4-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="690d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="690d4-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="690d4-106">Wartość [cor_pub_enumprocess —](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) wyliczenie, który określa typ procesu, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="690d4-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="690d4-107">W bieżącej wersji COR_PUB_MANAGEDONLY tylko jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="690d4-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="690d4-108">Wskaźnik na adres [icorpublishprocessenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) wystąpienia, które jest moduł wyliczający procesów.</span><span class="sxs-lookup"><span data-stu-id="690d4-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="690d4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="690d4-109">Remarks</span></span>  
 <span data-ttu-id="690d4-110">Moduł wyliczający kolekcja procesów opiera się na migawki procesów, które są uruchomione podczas `EnumProcesses` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="690d4-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="690d4-111">Moduł wyliczający nie będzie zawierać wszystkie procesy, które kończy się przed lub uruchom po `EnumProcesses` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="690d4-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="690d4-112">`EnumProcesses` Metoda może być wywoływana więcej niż raz w tym [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) wystąpienia, aby utworzyć nową kolekcję aktualne procesów.</span><span class="sxs-lookup"><span data-stu-id="690d4-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="690d4-113">Nie będzie mieć wpływ na istniejących kolekcji przez kolejne wywołania z `EnumProcesses` metody.</span><span class="sxs-lookup"><span data-stu-id="690d4-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="690d4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="690d4-114">Requirements</span></span>  
 <span data-ttu-id="690d4-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="690d4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="690d4-116">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="690d4-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="690d4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="690d4-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="690d4-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="690d4-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="690d4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="690d4-119">See also</span></span>

- [<span data-ttu-id="690d4-120">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="690d4-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
