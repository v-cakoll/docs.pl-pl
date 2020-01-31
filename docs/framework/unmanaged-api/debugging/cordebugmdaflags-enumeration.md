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
ms.openlocfilehash: 34a66a8afa118ecaaaeea0b7b78daaadf1da7509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778263"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="38372-102">CorDebugMDAFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38372-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="38372-103">Określa stan wątku, w którym jest uruchamiany Asystent debugowania zarządzanego (MDA).</span><span class="sxs-lookup"><span data-stu-id="38372-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38372-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38372-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="38372-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="38372-105">Members</span></span>  
  
|<span data-ttu-id="38372-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="38372-106">Member</span></span>|<span data-ttu-id="38372-107">Opis</span><span class="sxs-lookup"><span data-stu-id="38372-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="38372-108">Wątek, w którym zostało wywołane zdarzenie MDA, został wywołany od momentu uruchomienia MDA.</span><span class="sxs-lookup"><span data-stu-id="38372-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38372-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38372-109">Remarks</span></span>  
 <span data-ttu-id="38372-110">Gdy stos wywołań nie opisuje już, gdzie zdarzenie MDA zostało pierwotnie zgłoszone, wątek jest traktowany jako *poślizg*.</span><span class="sxs-lookup"><span data-stu-id="38372-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="38372-111">Jest to nietypowe działanie związane z wykonywaniem przez wątek nieprawidłowej operacji przy zamykaniu.</span><span class="sxs-lookup"><span data-stu-id="38372-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38372-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38372-112">Requirements</span></span>  
 <span data-ttu-id="38372-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38372-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38372-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38372-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38372-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38372-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38372-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38372-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38372-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38372-117">See also</span></span>

- [<span data-ttu-id="38372-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="38372-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
