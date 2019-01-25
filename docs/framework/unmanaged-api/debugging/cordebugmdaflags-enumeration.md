---
title: CorDebugMDAFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7f20dec86a85be85472037f58a2bd2002d9be1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620402"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="ffed0-102">CorDebugMDAFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ffed0-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="ffed0-103">Określa stan wątku, na którym jest uruchamiany zarządzanego Asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="ffed0-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffed0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffed0-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ffed0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ffed0-105">Members</span></span>  
  
|<span data-ttu-id="ffed0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ffed0-106">Member</span></span>|<span data-ttu-id="ffed0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ffed0-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="ffed0-108">Wątku, na którym zostało wywołane MDA jest przesuwane, ponieważ zostało wywołane MDA.</span><span class="sxs-lookup"><span data-stu-id="ffed0-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffed0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffed0-109">Remarks</span></span>  
 <span data-ttu-id="ffed0-110">Gdy stos wywołań nie jest już w tym artykule opisano gdzie MDA pierwotnie został zgłoszony, wątek jest uważany za *poślizgiem*.</span><span class="sxs-lookup"><span data-stu-id="ffed0-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="ffed0-111">Jest to nietypowych okoliczności spowodowanym ulepszonym wykonanie wątku Nieprawidłowa operacja podczas zamykania.</span><span class="sxs-lookup"><span data-stu-id="ffed0-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffed0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffed0-112">Requirements</span></span>  
 <span data-ttu-id="ffed0-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffed0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffed0-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffed0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffed0-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffed0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffed0-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffed0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffed0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffed0-117">See also</span></span>
- [<span data-ttu-id="ffed0-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ffed0-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
