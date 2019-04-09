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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157776"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="5ab01-102">ICorDebugObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ab01-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="5ab01-103">Implementuje metody ICorDebugEnum i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="5ab01-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ab01-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5ab01-104">Methods</span></span>  
  
|<span data-ttu-id="5ab01-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5ab01-105">Method</span></span>|<span data-ttu-id="5ab01-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5ab01-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ab01-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="5ab01-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="5ab01-108">Pobiera RVA o określoną liczbę obiektów z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="5ab01-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ab01-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ab01-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ab01-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="5ab01-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ab01-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ab01-111">Requirements</span></span>  
 <span data-ttu-id="5ab01-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab01-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab01-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ab01-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ab01-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ab01-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5ab01-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5ab01-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ab01-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ab01-116">See also</span></span>

- [<span data-ttu-id="5ab01-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5ab01-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
