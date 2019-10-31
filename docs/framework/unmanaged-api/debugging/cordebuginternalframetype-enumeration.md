---
title: CorDebugInternalFrameType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: e76800316885c27c697421d454341d5f0789c611
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097952"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="e00b6-102">CorDebugInternalFrameType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e00b6-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="e00b6-103">Identyfikuje typ ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e00b6-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="e00b6-104">To wyliczenie jest używane przez metodę [ICorDebugInternalFrame:: GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e00b6-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e00b6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e00b6-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="e00b6-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e00b6-106">Members</span></span>  
  
|<span data-ttu-id="e00b6-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e00b6-107">Member</span></span>|<span data-ttu-id="e00b6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e00b6-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="e00b6-109">Wartość null.</span><span class="sxs-lookup"><span data-stu-id="e00b6-109">A null value.</span></span> <span data-ttu-id="e00b6-110">Metoda `ICorDebugInternalFrame::GetFrameType` nigdy nie zwraca tej wartości.</span><span class="sxs-lookup"><span data-stu-id="e00b6-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="e00b6-111">Ramka klasy zarządzanej do niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="e00b6-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="e00b6-112">Niezarządzana ramka zastępcza niezarządzana.</span><span class="sxs-lookup"><span data-stu-id="e00b6-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="e00b6-113">Przejście między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e00b6-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="e00b6-114">Uproszczone wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="e00b6-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="e00b6-115">Rozpoczęcie obliczania funkcji.</span><span class="sxs-lookup"><span data-stu-id="e00b6-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="e00b6-116">Wewnętrzne wywołanie środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e00b6-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="e00b6-117">Rozpoczęcie inicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="e00b6-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="e00b6-118">Wyjątek, który jest generowany.</span><span class="sxs-lookup"><span data-stu-id="e00b6-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="e00b6-119">Ramka używana do zabezpieczenia dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="e00b6-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="e00b6-120">Środowisko uruchomieniowe to JIT-kompiluje metodę.</span><span class="sxs-lookup"><span data-stu-id="e00b6-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e00b6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e00b6-121">Requirements</span></span>  
 <span data-ttu-id="e00b6-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e00b6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e00b6-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e00b6-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e00b6-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e00b6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e00b6-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e00b6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e00b6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e00b6-126">See also</span></span>

- [<span data-ttu-id="e00b6-127">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e00b6-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
