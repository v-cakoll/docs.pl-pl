---
title: Wyliczenie CorDebugCodeInvokePurpose
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: 2e59d02093b9c2e2bda72c45de25975cbbdb7a29
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796018"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="09776-102">Wyliczenie CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="09776-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="09776-103">Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="09776-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09776-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09776-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="09776-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="09776-105">Members</span></span>  
  
|<span data-ttu-id="09776-106">Członek</span><span class="sxs-lookup"><span data-stu-id="09776-106">Member</span></span>|<span data-ttu-id="09776-107">Opis</span><span class="sxs-lookup"><span data-stu-id="09776-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="09776-108">Brak lub nieznany.</span><span class="sxs-lookup"><span data-stu-id="09776-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="09776-109">Kod zarządzany będzie uruchamiał każdy zarządzany punkt wejścia, taki jak odwrotne wywołanie p.</span><span class="sxs-lookup"><span data-stu-id="09776-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="09776-110">Każdy bardziej szczegółowy cel jest nieznany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="09776-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="09776-111">Kod zarządzany będzie uruchamiał Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="09776-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="09776-112">Kod zarządzany uruchomi implementację dla pewnej metody interfejsu, która została wywołana.</span><span class="sxs-lookup"><span data-stu-id="09776-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09776-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09776-113">Remarks</span></span>  
 <span data-ttu-id="09776-114">To wyliczenie jest używane przez metodę [Metoda ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) w celu uzyskania informacji na temat wykonywania kroków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="09776-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09776-115">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="09776-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09776-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09776-116">Requirements</span></span>  
 <span data-ttu-id="09776-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09776-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09776-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09776-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09776-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09776-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09776-120">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09776-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09776-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09776-121">See also</span></span>

- [<span data-ttu-id="09776-122">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="09776-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="09776-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="09776-123">Debugging</span></span>](index.md)
