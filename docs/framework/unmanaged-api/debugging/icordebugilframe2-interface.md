---
title: ICorDebugILFrame2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccb39609b37aff09ac7890df562d6c08e3c3c159
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412438"
---
# <a name="icordebugilframe2-interface1"></a><span data-ttu-id="a2c49-102">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="a2c49-102">ICorDebugILFrame2 Interface1</span></span>
<span data-ttu-id="a2c49-103">Logiczne rozszerzenie interfejsu ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="a2c49-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2c49-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a2c49-104">Methods</span></span>  
  
|<span data-ttu-id="a2c49-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a2c49-105">Method</span></span>|<span data-ttu-id="a2c49-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a2c49-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2c49-107">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="a2c49-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="a2c49-108">Pobiera obiekt ICorDebugTypeEnum zawierający <xref:System.Type> parametrów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="a2c49-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="a2c49-109">RemapFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="a2c49-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="a2c49-110">Ponownie mapuje funkcję edytowany przez określenie nowego przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="a2c49-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2c49-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2c49-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2c49-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="a2c49-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c49-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2c49-113">Requirements</span></span>  
 <span data-ttu-id="a2c49-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c49-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c49-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2c49-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2c49-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2c49-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2c49-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c49-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c49-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2c49-118">See Also</span></span>  
 [<span data-ttu-id="a2c49-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a2c49-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
