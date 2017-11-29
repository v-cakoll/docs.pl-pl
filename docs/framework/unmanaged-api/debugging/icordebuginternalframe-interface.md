---
title: ICorDebugInternalFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame
helpviewer_keywords: ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a05ba891e734fbf5a94b2a1f91e29d484e1c788b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="fa274-102">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="fa274-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="fa274-103">Reprezentuje wewnętrzny czasu wykonywania ramki na stosie.</span><span class="sxs-lookup"><span data-stu-id="fa274-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="fa274-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="fa274-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa274-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fa274-105">Methods</span></span>  
  
|<span data-ttu-id="fa274-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fa274-106">Method</span></span>|<span data-ttu-id="fa274-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fa274-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa274-108">GetFrameType — metoda</span><span class="sxs-lookup"><span data-stu-id="fa274-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="fa274-109">Pobiera typ tej ramki wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="fa274-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa274-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa274-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa274-111">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="fa274-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa274-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa274-112">Requirements</span></span>  
 <span data-ttu-id="fa274-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa274-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa274-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa274-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa274-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa274-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa274-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa274-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa274-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa274-117">See Also</span></span>  
 [<span data-ttu-id="fa274-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="fa274-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
