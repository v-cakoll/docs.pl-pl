---
title: ICorDebugDataTarget3 — interfejs
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 57ef9b567d57c77c523ca6daefcf80b1d7de66d1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976411"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="ab5a5-102">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ab5a5-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="ab5a5-103">Logicznie rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu dostarczenia informacji o załadowanych modułach.</span><span class="sxs-lookup"><span data-stu-id="ab5a5-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="ab5a5-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab5a5-104">Method</span></span>  
  
|<span data-ttu-id="ab5a5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab5a5-105">Method</span></span>|<span data-ttu-id="ab5a5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ab5a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab5a5-107">GetLoadedModules, metoda</span><span class="sxs-lookup"><span data-stu-id="ab5a5-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="ab5a5-108">Pobiera listę modułów, które zostały wcześniej załadowane.</span><span class="sxs-lookup"><span data-stu-id="ab5a5-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab5a5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab5a5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab5a5-110">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ab5a5-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ab5a5-111">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="ab5a5-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab5a5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab5a5-112">Requirements</span></span>  
 <span data-ttu-id="ab5a5-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab5a5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab5a5-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab5a5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab5a5-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab5a5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab5a5-116">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab5a5-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5a5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab5a5-117">See also</span></span>

- [<span data-ttu-id="ab5a5-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ab5a5-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ab5a5-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ab5a5-119">Debugging</span></span>](index.md)
