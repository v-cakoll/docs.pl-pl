---
title: LoggingLevelEnum — Wyliczenie
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 01e1eafd9955a0876f77e34eb73c2a3fc6d815c2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139201"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="71525-102">LoggingLevelEnum — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="71525-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="71525-103">Wskazuje poziom ważności komunikatu opisowego, który jest zapisywana w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="71525-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71525-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71525-104">Syntax</span></span>  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="71525-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="71525-105">Members</span></span>  
  
|<span data-ttu-id="71525-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="71525-106">Member</span></span>|<span data-ttu-id="71525-107">Opis</span><span class="sxs-lookup"><span data-stu-id="71525-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="71525-108">Komunikat jest poziomem śledzenia równym 0.</span><span class="sxs-lookup"><span data-stu-id="71525-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="71525-109">Komunikat jest poziomem śledzenia 1.</span><span class="sxs-lookup"><span data-stu-id="71525-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="71525-110">Komunikat jest poziomem śledzenia 2.</span><span class="sxs-lookup"><span data-stu-id="71525-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="71525-111">Komunikat jest poziomem śledzenia 3.</span><span class="sxs-lookup"><span data-stu-id="71525-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="71525-112">Komunikat jest poziomem śledzenia 4.</span><span class="sxs-lookup"><span data-stu-id="71525-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="71525-113">Komunikat jest poziomem stanu 0.</span><span class="sxs-lookup"><span data-stu-id="71525-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="71525-114">Komunikat jest poziomem stanu 1.</span><span class="sxs-lookup"><span data-stu-id="71525-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="71525-115">Komunikat jest poziomem stanu 2.</span><span class="sxs-lookup"><span data-stu-id="71525-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="71525-116">Komunikat jest poziomem stanu 3.</span><span class="sxs-lookup"><span data-stu-id="71525-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="71525-117">Komunikat jest poziomem stanu 4.</span><span class="sxs-lookup"><span data-stu-id="71525-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="71525-118">Komunikat jest poziomem ostrzegawczym.</span><span class="sxs-lookup"><span data-stu-id="71525-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="71525-119">Komunikat jest poziomem błędu.</span><span class="sxs-lookup"><span data-stu-id="71525-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="71525-120">Komunikat jest poziomem awaryjnego.</span><span class="sxs-lookup"><span data-stu-id="71525-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71525-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71525-121">Remarks</span></span>  
 <span data-ttu-id="71525-122">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje metodę [ICorDebugManagedCallback:: LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) w celu powiadomienia debugera o zarejestrowaniu zdarzenia przez wątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="71525-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="71525-123">Środowisko CLR przekazuje wartość wyliczenia `LoggingLevelEnum`, aby wskazać poziom ważności komunikatu, który został zapisany przez wątek zarządzany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71525-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71525-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71525-124">Requirements</span></span>  
 <span data-ttu-id="71525-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71525-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71525-126">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="71525-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71525-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="71525-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71525-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71525-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71525-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71525-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="71525-130">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="71525-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
