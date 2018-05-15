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
ms.openlocfilehash: 2779138a0999e34ad6424d76ddfebbcfdf611d58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="3380d-102">ICorPublish::EnumProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="3380d-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="3380d-103">Pobiera moduł wyliczający dla zarządzanych procesów uruchomionych na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3380d-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3380d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3380d-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3380d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3380d-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="3380d-106">Wartość [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) wyliczenie określający typ procesu, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="3380d-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="3380d-107">W bieżącej wersji tylko COR_PUB_MANAGEDONLY jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="3380d-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="3380d-108">Wskaźnik do adresu [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) wystąpienie, które jest modułem wyliczającym procesów.</span><span class="sxs-lookup"><span data-stu-id="3380d-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3380d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3380d-109">Remarks</span></span>  
 <span data-ttu-id="3380d-110">Moduł wyliczający kolekcja procesów jest oparta na migawki procesów, które są uruchomione podczas obliczania `EnumProcesses` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3380d-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="3380d-111">Moduł wyliczający nie będzie zawierać wszystkie procesy, które kończy się przed lub uruchomić po `EnumProcesses` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3380d-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="3380d-112">`EnumProcesses` — Metoda może być wywołany więcej niż raz w tym [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) wystąpienia, aby utworzyć nową kolekcję aktualne procesów.</span><span class="sxs-lookup"><span data-stu-id="3380d-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="3380d-113">Nie wpłynie istniejących zbiorach przez kolejne wywołania `EnumProcesses` metody.</span><span class="sxs-lookup"><span data-stu-id="3380d-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3380d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3380d-114">Requirements</span></span>  
 <span data-ttu-id="3380d-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3380d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3380d-116">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3380d-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3380d-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3380d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3380d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3380d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3380d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3380d-119">See Also</span></span>  
 [<span data-ttu-id="3380d-120">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="3380d-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
