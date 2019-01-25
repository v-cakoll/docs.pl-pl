---
title: ICorDebugLoadedModule — interfejs
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8f3a881a1beceb7d4aa35e2bd9a5e9e5419a391
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654870"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="6b103-102">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="6b103-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="6b103-103">Zawiera informacje dotyczące załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="6b103-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b103-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6b103-104">Methods</span></span>  
  
|<span data-ttu-id="6b103-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6b103-105">Method</span></span>|<span data-ttu-id="6b103-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6b103-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b103-107">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="6b103-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="6b103-108">Pobiera adres podstawowy załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="6b103-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="6b103-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="6b103-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="6b103-110">Pobiera nazwę załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="6b103-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="6b103-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="6b103-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="6b103-112">Pobiera rozmiar w bajtach załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="6b103-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b103-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b103-113">Remarks</span></span>  
 <span data-ttu-id="6b103-114">`ICorDebugLoadedModule` Interfejs jest implementowany przez debugera i jest używany przez środowisko CLR, debugowanie, interfejsy, aby uzyskać informacje na temat załadowanym module z debugera.</span><span class="sxs-lookup"><span data-stu-id="6b103-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b103-115">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6b103-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6b103-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="6b103-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b103-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b103-117">Requirements</span></span>  
 <span data-ttu-id="6b103-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b103-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b103-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b103-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b103-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b103-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b103-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b103-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b103-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b103-122">See also</span></span>
- [<span data-ttu-id="6b103-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6b103-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6b103-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6b103-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
