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
ms.openlocfilehash: 826dfceb28512e4fd3157c432b7a4d94fba704fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097861"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="c3655-102">CorDebugNGenPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c3655-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="c3655-103">Zapewnia wartość określającą, czy debuger ładuje obrazy natywne (NGen) z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="c3655-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3655-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3655-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="c3655-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3655-105">Members</span></span>  
  
|<span data-ttu-id="c3655-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c3655-106">Member name</span></span>|<span data-ttu-id="c3655-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c3655-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="c3655-108">W aplikacji [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] użycie obrazów z lokalnej pamięci podręcznej obrazów natywnych jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="c3655-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="c3655-109">W aplikacji klasycznej to ustawienie nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="c3655-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3655-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3655-110">Remarks</span></span>  
 <span data-ttu-id="c3655-111">Wyliczenie `CorDebugNGENPolicy` jest używane przez metodę [ICorDebugProcess5:: EnableNGENPolicy —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3655-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="c3655-112">Wyłączenie używania obrazów z lokalnej pamięci podręcznej obrazów natywnych zapewnia spójne środowisko debugowania przez zagwarantowanie, że debuger ładuje obrazy skompilowane JIT możliwością debugowania zamiast zoptymalizowanych obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="c3655-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3655-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3655-113">Requirements</span></span>  
 <span data-ttu-id="c3655-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3655-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3655-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3655-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3655-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c3655-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3655-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3655-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3655-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3655-118">See also</span></span>

- [<span data-ttu-id="c3655-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3655-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
