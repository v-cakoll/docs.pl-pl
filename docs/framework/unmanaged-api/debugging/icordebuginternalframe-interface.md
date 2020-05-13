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
ms.openlocfilehash: 332bc99795c0a4c896b60c61941a5a24b3f4accc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209946"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="5d342-102">ICorDebugInternalFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="5d342-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="5d342-103">Reprezentuje wewnętrzną ramkę środowiska uruchomieniowego na stosie.</span><span class="sxs-lookup"><span data-stu-id="5d342-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="5d342-104">Ten interfejs jest podklasą interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="5d342-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d342-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5d342-105">Methods</span></span>  
  
|<span data-ttu-id="5d342-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d342-106">Method</span></span>|<span data-ttu-id="5d342-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5d342-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d342-108">GetFrameType, metoda</span><span class="sxs-lookup"><span data-stu-id="5d342-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="5d342-109">Pobiera typ tej wewnętrznej ramki.</span><span class="sxs-lookup"><span data-stu-id="5d342-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d342-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d342-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d342-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="5d342-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d342-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d342-112">Requirements</span></span>  
 <span data-ttu-id="5d342-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d342-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d342-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d342-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d342-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5d342-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d342-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d342-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d342-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d342-117">See also</span></span>

- [<span data-ttu-id="5d342-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5d342-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
