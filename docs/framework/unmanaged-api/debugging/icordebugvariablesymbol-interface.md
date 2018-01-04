---
title: Interfejs ICorDebugVariableSymbol
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a09fab1468435212c4437c58c113691e049b1ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="0a8e9-102">Interfejs ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="0a8e9-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="0a8e9-103">Pobiera informacje o symbolu debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a8e9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0a8e9-104">Methods</span></span>  
  
|<span data-ttu-id="0a8e9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a8e9-105">Method</span></span>|<span data-ttu-id="0a8e9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0a8e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a8e9-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="0a8e9-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="0a8e9-108">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="0a8e9-109">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="0a8e9-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="0a8e9-110">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="0a8e9-111">GetSlotIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="0a8e9-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="0a8e9-112">Pobiera indeks gniazda zarządzanych zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="0a8e9-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="0a8e9-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="0a8e9-114">Pobiera wartość zmiennej w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="0a8e9-115">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="0a8e9-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="0a8e9-116">Przypisuje wartość tablica bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a8e9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a8e9-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a8e9-118">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0a8e9-119">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a8e9-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a8e9-120">Requirements</span></span>  
 <span data-ttu-id="0a8e9-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a8e9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a8e9-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a8e9-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a8e9-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a8e9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a8e9-124">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a8e9-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8e9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a8e9-125">See Also</span></span>  
 [<span data-ttu-id="0a8e9-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0a8e9-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0a8e9-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0a8e9-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
