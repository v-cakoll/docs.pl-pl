---
title: ICorDebugLoadedModule — interfejs
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9da6aba61382381fc25fe70615976cd0e744ee1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910004"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="7c165-102">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="7c165-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="7c165-103">Zawiera informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="7c165-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c165-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7c165-104">Methods</span></span>  
  
|<span data-ttu-id="7c165-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c165-105">Method</span></span>|<span data-ttu-id="7c165-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7c165-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c165-107">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="7c165-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="7c165-108">Pobiera adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="7c165-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="7c165-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="7c165-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="7c165-110">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="7c165-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="7c165-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="7c165-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="7c165-112">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="7c165-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c165-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c165-113">Remarks</span></span>  
 <span data-ttu-id="7c165-114">`ICorDebugLoadedModule` Interfejs jest implementowany przez debuger i jest używany przez interfejsy debugowania CLR do uzyskiwania informacji o załadowanym module z debugera.</span><span class="sxs-lookup"><span data-stu-id="7c165-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c165-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7c165-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7c165-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="7c165-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c165-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c165-117">Requirements</span></span>  
 <span data-ttu-id="7c165-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c165-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c165-119">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c165-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c165-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c165-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c165-121">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c165-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c165-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c165-122">See also</span></span>

- [<span data-ttu-id="7c165-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7c165-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7c165-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7c165-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
