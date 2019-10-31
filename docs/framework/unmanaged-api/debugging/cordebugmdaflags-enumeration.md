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
ms.openlocfilehash: c7af194351290ad937e40a2fc8b960c2c242629c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132793"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="5ced4-102">CorDebugMDAFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5ced4-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="5ced4-103">Określa stan wątku, w którym jest uruchamiany Asystent debugowania zarządzanego (MDA).</span><span class="sxs-lookup"><span data-stu-id="5ced4-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ced4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ced4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5ced4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5ced4-105">Members</span></span>  
  
|<span data-ttu-id="5ced4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5ced4-106">Member</span></span>|<span data-ttu-id="5ced4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5ced4-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="5ced4-108">Wątek, w którym zostało wywołane zdarzenie MDA, został wywołany od momentu uruchomienia MDA.</span><span class="sxs-lookup"><span data-stu-id="5ced4-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ced4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ced4-109">Remarks</span></span>  
 <span data-ttu-id="5ced4-110">Gdy stos wywołań nie opisuje już, gdzie zdarzenie MDA zostało pierwotnie zgłoszone, wątek jest traktowany jako *poślizg*.</span><span class="sxs-lookup"><span data-stu-id="5ced4-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="5ced4-111">Jest to nietypowe działanie związane z wykonywaniem przez wątek nieprawidłowej operacji przy zamykaniu.</span><span class="sxs-lookup"><span data-stu-id="5ced4-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ced4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ced4-112">Requirements</span></span>  
 <span data-ttu-id="5ced4-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ced4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ced4-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5ced4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ced4-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5ced4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ced4-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ced4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ced4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ced4-117">See also</span></span>

- [<span data-ttu-id="5ced4-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5ced4-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
