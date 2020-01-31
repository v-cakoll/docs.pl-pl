---
title: ICorDebugDataTarget3 — interfejs
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 04e7b9a064d4a06a06b8a1518f06092ba79a3561
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783492"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="b2aab-102">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2aab-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="b2aab-103">Logicznie rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu dostarczenia informacji o załadowanych modułach.</span><span class="sxs-lookup"><span data-stu-id="b2aab-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="b2aab-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2aab-104">Method</span></span>  
  
|<span data-ttu-id="b2aab-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2aab-105">Method</span></span>|<span data-ttu-id="b2aab-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b2aab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2aab-107">GetLoadedModules, metoda</span><span class="sxs-lookup"><span data-stu-id="b2aab-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="b2aab-108">Pobiera listę modułów, które zostały wcześniej załadowane.</span><span class="sxs-lookup"><span data-stu-id="b2aab-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2aab-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2aab-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2aab-110">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b2aab-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b2aab-111">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="b2aab-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2aab-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2aab-112">Requirements</span></span>  
 <span data-ttu-id="b2aab-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2aab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2aab-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2aab-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2aab-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2aab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2aab-116">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2aab-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2aab-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2aab-117">See also</span></span>

- [<span data-ttu-id="b2aab-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b2aab-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b2aab-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b2aab-119">Debugging</span></span>](index.md)
