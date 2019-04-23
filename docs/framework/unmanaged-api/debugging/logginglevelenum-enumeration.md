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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086510"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="8aec8-102">LoggingLevelEnum — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8aec8-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="8aec8-103">Wskazuje poziom ważności opisowy komunikat, który jest zapisywany w dzienniku zdarzeń, gdy wątków zarządzanych rejestruje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="8aec8-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aec8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8aec8-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="8aec8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8aec8-105">Members</span></span>  
  
|<span data-ttu-id="8aec8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8aec8-106">Member</span></span>|<span data-ttu-id="8aec8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8aec8-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="8aec8-108">Komunikat jest poziom śledzenia 0.</span><span class="sxs-lookup"><span data-stu-id="8aec8-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="8aec8-109">Komunikat jest poziom śledzenia 1.</span><span class="sxs-lookup"><span data-stu-id="8aec8-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="8aec8-110">Komunikat jest poziom śledzenia 2.</span><span class="sxs-lookup"><span data-stu-id="8aec8-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="8aec8-111">Komunikat jest poziom śledzenia 3.</span><span class="sxs-lookup"><span data-stu-id="8aec8-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="8aec8-112">Komunikat jest poziom śledzenia 4.</span><span class="sxs-lookup"><span data-stu-id="8aec8-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="8aec8-113">Komunikat jest poziom stanu 0.</span><span class="sxs-lookup"><span data-stu-id="8aec8-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="8aec8-114">Komunikat jest poziom stanu 1.</span><span class="sxs-lookup"><span data-stu-id="8aec8-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="8aec8-115">Komunikat jest poziom stanu 2.</span><span class="sxs-lookup"><span data-stu-id="8aec8-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="8aec8-116">Komunikat jest poziom stanu 3.</span><span class="sxs-lookup"><span data-stu-id="8aec8-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="8aec8-117">Komunikat jest poziom stanu 4.</span><span class="sxs-lookup"><span data-stu-id="8aec8-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="8aec8-118">Komunikat jest poziom ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="8aec8-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="8aec8-119">Komunikat jest poziomu błędu.</span><span class="sxs-lookup"><span data-stu-id="8aec8-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="8aec8-120">Komunikat jest alarm poziom.</span><span class="sxs-lookup"><span data-stu-id="8aec8-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aec8-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8aec8-121">Remarks</span></span>  
 <span data-ttu-id="8aec8-122">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) metodę, aby powiadomić debugera, że wątków zarządzanych jest rejestrowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="8aec8-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="8aec8-123">Środowisko CLR przekazuje wartość `LoggingLevelEnum` wyliczenie, aby wskazać poziom ważności komunikatu, który napisał wątków zarządzanych, w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8aec8-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aec8-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8aec8-124">Requirements</span></span>  
 <span data-ttu-id="8aec8-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aec8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aec8-126">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8aec8-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8aec8-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aec8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aec8-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aec8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aec8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8aec8-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="8aec8-130">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8aec8-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
