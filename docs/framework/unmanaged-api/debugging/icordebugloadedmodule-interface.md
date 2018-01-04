---
title: "ICorDebugLoadedModule — interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cc7a36deb7c81ccf67427b833dead7127619b39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="38300-102">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="38300-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="38300-103">Udostępnia informacje na temat załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="38300-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38300-104">Metody</span><span class="sxs-lookup"><span data-stu-id="38300-104">Methods</span></span>  
  
|<span data-ttu-id="38300-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="38300-105">Method</span></span>|<span data-ttu-id="38300-106">Opis</span><span class="sxs-lookup"><span data-stu-id="38300-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38300-107">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="38300-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="38300-108">Pobiera adres podstawowy załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="38300-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="38300-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="38300-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="38300-110">Pobiera nazwę załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="38300-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="38300-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="38300-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="38300-112">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="38300-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38300-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38300-113">Remarks</span></span>  
 <span data-ttu-id="38300-114">`ICorDebugLoadedModule` Interfejs jest implementowany przez debugera i jest używany przez środowisko CLR debugowania interfejsów można pobrać informacji o module załadowany z debugera.</span><span class="sxs-lookup"><span data-stu-id="38300-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38300-115">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="38300-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="38300-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="38300-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38300-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38300-117">Requirements</span></span>  
 <span data-ttu-id="38300-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38300-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38300-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38300-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38300-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38300-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38300-121">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38300-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38300-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38300-122">See Also</span></span>  
 [<span data-ttu-id="38300-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="38300-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="38300-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="38300-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
