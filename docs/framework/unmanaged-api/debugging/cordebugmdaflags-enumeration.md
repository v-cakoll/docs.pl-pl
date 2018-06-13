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
ms.openlocfilehash: ac4a8a0c13ba6aa0d5c65ec7fa1aa3b771c964eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404862"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="bf61c-102">CorDebugMDAFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bf61c-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="bf61c-103">Określa stan wątku, na którym jest uruchamiany zarządzany Asystent debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="bf61c-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf61c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf61c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bf61c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bf61c-105">Members</span></span>  
  
|<span data-ttu-id="bf61c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bf61c-106">Member</span></span>|<span data-ttu-id="bf61c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf61c-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="bf61c-108">Wątek, na którym zostało zainicjowane MDA jest przesuwane, ponieważ MDA zostało zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="bf61c-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf61c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf61c-109">Remarks</span></span>  
 <span data-ttu-id="bf61c-110">Gdy stos wywołań nie opisano, gdzie MDA pierwotnie został zgłoszony, wątek jest uważany za *poślizgiem*.</span><span class="sxs-lookup"><span data-stu-id="bf61c-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="bf61c-111">Jest to rzadko okoliczności spowodowanych wykonanie wątku Nieprawidłowa operacja podczas zamykania programu.</span><span class="sxs-lookup"><span data-stu-id="bf61c-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf61c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf61c-112">Requirements</span></span>  
 <span data-ttu-id="bf61c-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf61c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf61c-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf61c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf61c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf61c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf61c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf61c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf61c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf61c-117">See Also</span></span>  
 [<span data-ttu-id="bf61c-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="bf61c-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
