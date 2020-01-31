---
title: ICorDebugLoadedModule — interfejs
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9d3bdcec9e90dab337b595294d114de4bd3d531f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782001"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="00465-102">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="00465-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="00465-103">Zawiera informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="00465-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00465-104">Metody</span><span class="sxs-lookup"><span data-stu-id="00465-104">Methods</span></span>  
  
|<span data-ttu-id="00465-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="00465-105">Method</span></span>|<span data-ttu-id="00465-106">Opis</span><span class="sxs-lookup"><span data-stu-id="00465-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00465-107">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="00465-107">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="00465-108">Pobiera adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="00465-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="00465-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="00465-109">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="00465-110">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="00465-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="00465-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="00465-111">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="00465-112">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="00465-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00465-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00465-113">Remarks</span></span>  
 <span data-ttu-id="00465-114">Interfejs `ICorDebugLoadedModule` jest implementowany przez debuger i jest używany przez interfejsy debugowania CLR do uzyskiwania informacji o załadowanym module z debugera.</span><span class="sxs-lookup"><span data-stu-id="00465-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00465-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="00465-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="00465-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="00465-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00465-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00465-117">Requirements</span></span>  
 <span data-ttu-id="00465-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00465-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00465-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00465-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00465-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="00465-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00465-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00465-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00465-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00465-122">See also</span></span>

- [<span data-ttu-id="00465-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="00465-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="00465-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="00465-124">Debugging</span></span>](index.md)
