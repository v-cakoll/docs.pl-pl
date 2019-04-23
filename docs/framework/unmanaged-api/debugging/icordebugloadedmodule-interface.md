---
title: ICorDebugLoadedModule — interfejs
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200756"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="657c9-102">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="657c9-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="657c9-103">Zawiera informacje dotyczące załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="657c9-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="657c9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="657c9-104">Methods</span></span>  
  
|<span data-ttu-id="657c9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="657c9-105">Method</span></span>|<span data-ttu-id="657c9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="657c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="657c9-107">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="657c9-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="657c9-108">Pobiera adres podstawowy załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="657c9-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="657c9-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="657c9-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="657c9-110">Pobiera nazwę załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="657c9-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="657c9-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="657c9-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="657c9-112">Pobiera rozmiar w bajtach załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="657c9-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="657c9-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="657c9-113">Remarks</span></span>  
 <span data-ttu-id="657c9-114">`ICorDebugLoadedModule` Interfejs jest implementowany przez debugera i jest używany przez środowisko CLR, debugowanie, interfejsy, aby uzyskać informacje na temat załadowanym module z debugera.</span><span class="sxs-lookup"><span data-stu-id="657c9-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="657c9-115">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="657c9-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="657c9-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="657c9-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="657c9-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="657c9-117">Requirements</span></span>  
 <span data-ttu-id="657c9-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="657c9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="657c9-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="657c9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="657c9-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="657c9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="657c9-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="657c9-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657c9-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="657c9-122">See also</span></span>

- [<span data-ttu-id="657c9-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="657c9-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="657c9-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="657c9-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
