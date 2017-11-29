---
title: "CorDebugNGenPolicy — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugNGenPolicy
helpviewer_keywords: CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6042d5232995e68a4f59dfa68093446a03badfd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="e0f80-102">CorDebugNGenPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e0f80-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="e0f80-103">Zawiera wartość, która określa, czy debuger ładuje obrazów natywnych (NGen) z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e0f80-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0f80-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="e0f80-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e0f80-105">Members</span></span>  
  
|<span data-ttu-id="e0f80-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="e0f80-106">Member name</span></span>|<span data-ttu-id="e0f80-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e0f80-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="e0f80-108">W [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikacji, użyj obrazów z pamięci podręcznej obrazów natywnych lokalnej jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="e0f80-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="e0f80-109">W aplikacji komputerowej to ustawienie nie ma żadnego skutku.</span><span class="sxs-lookup"><span data-stu-id="e0f80-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0f80-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0f80-110">Remarks</span></span>  
 <span data-ttu-id="e0f80-111">`CorDebugNGENPolicy` Wyliczenie jest używany przez [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e0f80-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="e0f80-112">Wyłączanie korzystania z obrazów z pamięci podręcznej obrazów natywnych lokalnej zapewnia spójne środowisko debugowania przez zapewnienie, że debuger ładuje możliwością debugowania kompilacji JIT obrazów zamiast zoptymalizowane obrazów macierzystych.</span><span class="sxs-lookup"><span data-stu-id="e0f80-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0f80-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0f80-113">Requirements</span></span>  
 <span data-ttu-id="e0f80-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0f80-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f80-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0f80-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0f80-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0f80-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0f80-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f80-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f80-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0f80-118">See Also</span></span>  
 [<span data-ttu-id="e0f80-119">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e0f80-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
