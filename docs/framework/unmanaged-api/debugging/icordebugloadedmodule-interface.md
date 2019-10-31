---
title: ICorDebugLoadedModule — interfejs
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9fe36497844b9c33cefcf8c63711941196847525
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122619"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="0e2f3-102">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="0e2f3-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="0e2f3-103">Zawiera informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="0e2f3-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e2f3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e2f3-104">Methods</span></span>  
  
|<span data-ttu-id="0e2f3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e2f3-105">Method</span></span>|<span data-ttu-id="0e2f3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0e2f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e2f3-107">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="0e2f3-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="0e2f3-108">Pobiera adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="0e2f3-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="0e2f3-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="0e2f3-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="0e2f3-110">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="0e2f3-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="0e2f3-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="0e2f3-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="0e2f3-112">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="0e2f3-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e2f3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e2f3-113">Remarks</span></span>  
 <span data-ttu-id="0e2f3-114">Interfejs `ICorDebugLoadedModule` jest implementowany przez debuger i jest używany przez interfejsy debugowania CLR do uzyskiwania informacji o załadowanym module z debugera.</span><span class="sxs-lookup"><span data-stu-id="0e2f3-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e2f3-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0e2f3-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0e2f3-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0e2f3-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e2f3-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e2f3-117">Requirements</span></span>  
 <span data-ttu-id="0e2f3-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e2f3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e2f3-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0e2f3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e2f3-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0e2f3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e2f3-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e2f3-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e2f3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e2f3-122">See also</span></span>

- [<span data-ttu-id="0e2f3-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0e2f3-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0e2f3-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0e2f3-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
