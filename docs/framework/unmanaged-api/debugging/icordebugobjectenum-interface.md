---
title: ICorDebugObjectEnum Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a9f10301db488e4ca68ce5fdaf0ba767053d7d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547004"
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="6def3-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="6def3-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="6def3-103">Implementuje metody ICorDebugEnum i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="6def3-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6def3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6def3-104">Methods</span></span>  
  
|<span data-ttu-id="6def3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6def3-105">Method</span></span>|<span data-ttu-id="6def3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6def3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6def3-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="6def3-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="6def3-108">Pobiera RVA o określoną liczbę obiektów z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="6def3-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6def3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6def3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6def3-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="6def3-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6def3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6def3-111">Requirements</span></span>  
 <span data-ttu-id="6def3-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6def3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6def3-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6def3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6def3-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6def3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6def3-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6def3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6def3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6def3-116">See also</span></span>
- [<span data-ttu-id="6def3-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6def3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
