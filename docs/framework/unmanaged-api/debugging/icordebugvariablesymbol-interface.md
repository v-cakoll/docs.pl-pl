---
title: ICorDebugVariableSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 25ffa55eeeb82d6feaf5696ea96dae81774e3d70
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121914"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="b6459-102">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6459-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="b6459-103">Pobiera informacje o symbolach debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b6459-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6459-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b6459-104">Methods</span></span>  
  
|<span data-ttu-id="b6459-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b6459-105">Method</span></span>|<span data-ttu-id="b6459-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b6459-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6459-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="b6459-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="b6459-108">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b6459-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="b6459-109">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="b6459-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="b6459-110">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b6459-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="b6459-111">GetSlotIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="b6459-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="b6459-112">Pobiera indeks gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b6459-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="b6459-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="b6459-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="b6459-114">Pobiera wartość zmiennej jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="b6459-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="b6459-115">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="b6459-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="b6459-116">Przypisuje wartość tablicy bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b6459-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6459-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6459-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6459-118">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b6459-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b6459-119">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="b6459-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6459-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6459-120">Requirements</span></span>  
 <span data-ttu-id="b6459-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6459-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6459-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6459-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6459-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6459-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6459-124">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6459-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6459-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6459-125">See also</span></span>

- [<span data-ttu-id="b6459-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6459-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b6459-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b6459-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
