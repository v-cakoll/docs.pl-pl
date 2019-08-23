---
title: ICorDebugVariableSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967981"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="f20fa-102">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="f20fa-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="f20fa-103">Pobiera informacje o symbolach debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f20fa-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f20fa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f20fa-104">Methods</span></span>  
  
|<span data-ttu-id="f20fa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f20fa-105">Method</span></span>|<span data-ttu-id="f20fa-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f20fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f20fa-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="f20fa-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="f20fa-108">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f20fa-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="f20fa-109">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="f20fa-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="f20fa-110">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f20fa-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="f20fa-111">GetSlotIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="f20fa-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="f20fa-112">Pobiera indeks gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f20fa-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="f20fa-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f20fa-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="f20fa-114">Pobiera wartość zmiennej jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="f20fa-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="f20fa-115">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f20fa-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="f20fa-116">Przypisuje wartość tablicy bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f20fa-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f20fa-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f20fa-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f20fa-118">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f20fa-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f20fa-119">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="f20fa-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f20fa-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f20fa-120">Requirements</span></span>  
 <span data-ttu-id="f20fa-121">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f20fa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f20fa-122">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f20fa-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f20fa-123">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f20fa-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f20fa-124">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f20fa-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f20fa-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f20fa-125">See also</span></span>

- [<span data-ttu-id="f20fa-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f20fa-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f20fa-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f20fa-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
