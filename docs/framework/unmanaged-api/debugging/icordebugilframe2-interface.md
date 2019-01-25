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
ms.openlocfilehash: 0996fee88d37bbc826a4e012dc44ea9005008ae4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575518"
---
# <a name="icordebugilframe2-interface1"></a><span data-ttu-id="56b17-102">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="56b17-102">ICorDebugILFrame2 Interface1</span></span>
<span data-ttu-id="56b17-103">Logiczne rozszerzenie icordebugilframe — interfejs</span><span class="sxs-lookup"><span data-stu-id="56b17-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56b17-104">Metody</span><span class="sxs-lookup"><span data-stu-id="56b17-104">Methods</span></span>  
  
|<span data-ttu-id="56b17-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="56b17-105">Method</span></span>|<span data-ttu-id="56b17-106">Opis</span><span class="sxs-lookup"><span data-stu-id="56b17-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56b17-107">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="56b17-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="56b17-108">Pobiera obiekt zawierający icordebugtypeenum — <xref:System.Type> parametrów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="56b17-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="56b17-109">RemapFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="56b17-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="56b17-110">Ponownie mapuje przeprowadzono edycję funkcji, określając nowy przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="56b17-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56b17-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56b17-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56b17-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="56b17-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b17-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56b17-113">Requirements</span></span>  
 <span data-ttu-id="56b17-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56b17-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b17-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56b17-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56b17-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56b17-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56b17-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b17-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b17-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56b17-118">See also</span></span>
- [<span data-ttu-id="56b17-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="56b17-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
