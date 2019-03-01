---
title: ICorDebugObjectEnum — Interfejs
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
ms.openlocfilehash: 452216a2ba4e8013d107977d82eae1508b2aba78
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967766"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="160cd-102">ICorDebugObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="160cd-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="160cd-103">Implementuje metody ICorDebugEnum i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="160cd-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="160cd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="160cd-104">Methods</span></span>  
  
|<span data-ttu-id="160cd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="160cd-105">Method</span></span>|<span data-ttu-id="160cd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="160cd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="160cd-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="160cd-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="160cd-108">Pobiera RVA o określoną liczbę obiektów z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="160cd-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="160cd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="160cd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="160cd-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="160cd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="160cd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="160cd-111">Requirements</span></span>  
 <span data-ttu-id="160cd-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="160cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="160cd-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="160cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="160cd-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="160cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="160cd-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="160cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160cd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="160cd-116">See also</span></span>
- [<span data-ttu-id="160cd-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="160cd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
