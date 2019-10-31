---
title: ICorDebugInternalFrame — Interfejs
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
ms.openlocfilehash: b1ee5a155afa4e33340108e7295adef2309986cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122709"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="4594a-102">ICorDebugInternalFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4594a-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="4594a-103">Reprezentuje wewnętrzną ramkę środowiska uruchomieniowego na stosie.</span><span class="sxs-lookup"><span data-stu-id="4594a-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="4594a-104">Ten interfejs jest podklasą interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="4594a-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4594a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4594a-105">Methods</span></span>  
  
|<span data-ttu-id="4594a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4594a-106">Method</span></span>|<span data-ttu-id="4594a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4594a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4594a-108">GetFrameType, metoda</span><span class="sxs-lookup"><span data-stu-id="4594a-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="4594a-109">Pobiera typ tej wewnętrznej ramki.</span><span class="sxs-lookup"><span data-stu-id="4594a-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4594a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4594a-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4594a-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="4594a-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4594a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4594a-112">Requirements</span></span>  
 <span data-ttu-id="4594a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4594a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4594a-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4594a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4594a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4594a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4594a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4594a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4594a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4594a-117">See also</span></span>

- [<span data-ttu-id="4594a-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4594a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
