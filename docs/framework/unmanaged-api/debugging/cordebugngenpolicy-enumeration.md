---
title: CorDebugNGenPolicy — Wyliczenie
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ae40916807a86d1c9828080a6cb9e5c1d14c2ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671229"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="db7b0-102">CorDebugNGenPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="db7b0-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="db7b0-103">Zawiera wartość określającą, czy debuger wczytuje obrazów macierzystych (NGen) z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="db7b0-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db7b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db7b0-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="db7b0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="db7b0-105">Members</span></span>  
  
|<span data-ttu-id="db7b0-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="db7b0-106">Member name</span></span>|<span data-ttu-id="db7b0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="db7b0-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="db7b0-108">W [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikacji, użycie obrazów z pamięci podręcznej obrazów natywnych lokalnej jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="db7b0-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="db7b0-109">W przypadku aplikacji klasycznej to ustawienie nie obowiązuje.</span><span class="sxs-lookup"><span data-stu-id="db7b0-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db7b0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db7b0-110">Remarks</span></span>  
 <span data-ttu-id="db7b0-111">`CorDebugNGENPolicy` Wyliczenie jest używane przez [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="db7b0-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="db7b0-112">Wyłączanie użycie obrazów z pamięci podręcznej obrazów natywnych lokalnej zapewnia spójne środowisko debugowania, zapewniając, że debuger ładuje debugowania obrazów kompilowanego dokładnie na czas, zamiast zoptymalizowane obrazy natywne.</span><span class="sxs-lookup"><span data-stu-id="db7b0-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db7b0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db7b0-113">Requirements</span></span>  
 <span data-ttu-id="db7b0-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db7b0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db7b0-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db7b0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db7b0-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db7b0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db7b0-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db7b0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db7b0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db7b0-118">See also</span></span>
- [<span data-ttu-id="db7b0-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="db7b0-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
