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
ms.openlocfilehash: 732523935eec62bffbc15705bc93c97f14c90064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792720"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="2b339-102">CorDebugMDAFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2b339-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="2b339-103">Określa stan wątku, na którym jest uruchamiany zarządzanego Asystenta debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="2b339-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b339-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b339-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2b339-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2b339-105">Members</span></span>  
  
|<span data-ttu-id="2b339-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2b339-106">Member</span></span>|<span data-ttu-id="2b339-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2b339-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="2b339-108">Wątku, na którym zostało wywołane MDA jest przesuwane, ponieważ zostało wywołane MDA.</span><span class="sxs-lookup"><span data-stu-id="2b339-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b339-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b339-109">Remarks</span></span>  
 <span data-ttu-id="2b339-110">Gdy stos wywołań nie jest już w tym artykule opisano gdzie MDA pierwotnie został zgłoszony, wątek jest uważany za *poślizgiem*.</span><span class="sxs-lookup"><span data-stu-id="2b339-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="2b339-111">Jest to nietypowych okoliczności spowodowanym ulepszonym wykonanie wątku Nieprawidłowa operacja podczas zamykania.</span><span class="sxs-lookup"><span data-stu-id="2b339-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b339-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b339-112">Requirements</span></span>  
 <span data-ttu-id="2b339-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b339-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b339-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b339-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b339-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b339-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b339-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b339-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b339-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b339-117">See also</span></span>

- [<span data-ttu-id="2b339-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2b339-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
