---
title: ICorDebugILFrame2, interfejs
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
ms.openlocfilehash: a4f57f27ec92e7977b46ebfa5967b0590674d2a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113441"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="28435-102">ICorDebugILFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="28435-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="28435-103">Logiczne rozszerzenie icordebugilframe — interfejs</span><span class="sxs-lookup"><span data-stu-id="28435-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28435-104">Metody</span><span class="sxs-lookup"><span data-stu-id="28435-104">Methods</span></span>  
  
|<span data-ttu-id="28435-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="28435-105">Method</span></span>|<span data-ttu-id="28435-106">Opis</span><span class="sxs-lookup"><span data-stu-id="28435-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28435-107">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="28435-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="28435-108">Pobiera obiekt zawierający icordebugtypeenum — <xref:System.Type> parametrów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="28435-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="28435-109">RemapFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="28435-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="28435-110">Ponownie mapuje przeprowadzono edycję funkcji, określając nowy przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="28435-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28435-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28435-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28435-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="28435-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28435-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28435-113">Requirements</span></span>  
 <span data-ttu-id="28435-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28435-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28435-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28435-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28435-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28435-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="28435-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="28435-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="28435-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28435-118">See also</span></span>

- [<span data-ttu-id="28435-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="28435-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
