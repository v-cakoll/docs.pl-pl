---
title: ICorDebugObjectEnum, interfejs
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
ms.openlocfilehash: 0144539987f14bed83bfc9eab2f5ca26d2a609ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942392"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="f7038-102">ICorDebugObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7038-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="f7038-103">Implementuje metody ICorDebugEnum i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="f7038-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7038-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f7038-104">Methods</span></span>  
  
|<span data-ttu-id="f7038-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f7038-105">Method</span></span>|<span data-ttu-id="f7038-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f7038-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7038-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="f7038-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="f7038-108">Pobiera RVA o określoną liczbę obiektów z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="f7038-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7038-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7038-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7038-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="f7038-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7038-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7038-111">Requirements</span></span>  
 <span data-ttu-id="f7038-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7038-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7038-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7038-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7038-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7038-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7038-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7038-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7038-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7038-116">See also</span></span>

- [<span data-ttu-id="f7038-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f7038-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
