---
title: ICorDebugInternalFrame, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9764cdcd07a09f5192a8f43b9baa5be40305c40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910168"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="561cb-102">ICorDebugInternalFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="561cb-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="561cb-103">Reprezentuje wewnętrzną ramkę środowiska uruchomieniowego na stosie.</span><span class="sxs-lookup"><span data-stu-id="561cb-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="561cb-104">Ten interfejs jest podklasą interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="561cb-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="561cb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="561cb-105">Methods</span></span>  
  
|<span data-ttu-id="561cb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="561cb-106">Method</span></span>|<span data-ttu-id="561cb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="561cb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="561cb-108">GetFrameType, metoda</span><span class="sxs-lookup"><span data-stu-id="561cb-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="561cb-109">Pobiera typ tej wewnętrznej ramki.</span><span class="sxs-lookup"><span data-stu-id="561cb-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="561cb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="561cb-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="561cb-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="561cb-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="561cb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="561cb-112">Requirements</span></span>  
 <span data-ttu-id="561cb-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="561cb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561cb-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="561cb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="561cb-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="561cb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="561cb-116">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561cb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="561cb-117">See also</span></span>

- [<span data-ttu-id="561cb-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="561cb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
