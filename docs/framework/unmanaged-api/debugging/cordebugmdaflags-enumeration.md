---
title: "CorDebugMDAFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMDAFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMDAFlags
helpviewer_keywords: CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 827825e4012b421caa4e05702a6f1a1b863ac69d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="b4d2f-102">CorDebugMDAFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b4d2f-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="b4d2f-103">Określa stan wątku, na którym jest uruchamiany zarządzany Asystent debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="b4d2f-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4d2f-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b4d2f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b4d2f-105">Members</span></span>  
  
|<span data-ttu-id="b4d2f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b4d2f-106">Member</span></span>|<span data-ttu-id="b4d2f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4d2f-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="b4d2f-108">Wątek, na którym zostało zainicjowane MDA jest przesuwane, ponieważ MDA zostało zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="b4d2f-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d2f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4d2f-109">Remarks</span></span>  
 <span data-ttu-id="b4d2f-110">Gdy stos wywołań nie opisano, gdzie MDA pierwotnie został zgłoszony, wątek jest uważany za *poślizgiem*.</span><span class="sxs-lookup"><span data-stu-id="b4d2f-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="b4d2f-111">Jest to rzadko okoliczności spowodowanych wykonanie wątku Nieprawidłowa operacja podczas zamykania programu.</span><span class="sxs-lookup"><span data-stu-id="b4d2f-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d2f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4d2f-112">Requirements</span></span>  
 <span data-ttu-id="b4d2f-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d2f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d2f-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4d2f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4d2f-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4d2f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d2f-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d2f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d2f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4d2f-117">See Also</span></span>  
 [<span data-ttu-id="b4d2f-118">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b4d2f-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
