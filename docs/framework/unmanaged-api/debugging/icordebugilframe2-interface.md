---
title: ICorDebugILFrame2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2
helpviewer_keywords: ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 759232d5c1e5bdf00c85145fa0fc3d69743c13f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe2-interface1"></a><span data-ttu-id="3ac23-102">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="3ac23-102">ICorDebugILFrame2 Interface1</span></span>
<span data-ttu-id="3ac23-103">Logiczne rozszerzenie interfejsu ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="3ac23-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ac23-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3ac23-104">Methods</span></span>  
  
|<span data-ttu-id="3ac23-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ac23-105">Method</span></span>|<span data-ttu-id="3ac23-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3ac23-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ac23-107">EnumerateTypeParameters — metoda</span><span class="sxs-lookup"><span data-stu-id="3ac23-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="3ac23-108">Pobiera obiekt ICorDebugTypeEnum zawierający <xref:System.Type> parametrów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="3ac23-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="3ac23-109">RemapFunction — metoda</span><span class="sxs-lookup"><span data-stu-id="3ac23-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="3ac23-110">Ponownie mapuje funkcję edytowany przez określenie nowego przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="3ac23-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ac23-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ac23-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ac23-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="3ac23-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ac23-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ac23-113">Requirements</span></span>  
 <span data-ttu-id="3ac23-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ac23-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ac23-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ac23-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ac23-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ac23-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ac23-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ac23-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac23-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ac23-118">See Also</span></span>  
 [<span data-ttu-id="3ac23-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="3ac23-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
