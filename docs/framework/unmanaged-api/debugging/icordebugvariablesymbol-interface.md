---
title: ICorDebugVariableSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 412ecbfc03378947e5a578e163034d104718bc91
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397103"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="92dd1-102">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="92dd1-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="92dd1-103">Pobiera informacje o symbolach debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="92dd1-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92dd1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="92dd1-104">Methods</span></span>  
  
|<span data-ttu-id="92dd1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="92dd1-105">Method</span></span>|<span data-ttu-id="92dd1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="92dd1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92dd1-107">GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="92dd1-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="92dd1-108">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="92dd1-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="92dd1-109">GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="92dd1-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="92dd1-110">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="92dd1-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="92dd1-111">GetSlotIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="92dd1-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="92dd1-112">Pobiera indeks gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="92dd1-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="92dd1-113">GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="92dd1-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="92dd1-114">Pobiera wartość zmiennej jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="92dd1-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="92dd1-115">SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="92dd1-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="92dd1-116">Przypisuje wartość tablicy bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="92dd1-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92dd1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92dd1-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92dd1-118">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="92dd1-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="92dd1-119">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="92dd1-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92dd1-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92dd1-120">Requirements</span></span>  
 <span data-ttu-id="92dd1-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92dd1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92dd1-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92dd1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92dd1-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92dd1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92dd1-124">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92dd1-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92dd1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92dd1-125">See also</span></span>

- [<span data-ttu-id="92dd1-126">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="92dd1-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="92dd1-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="92dd1-127">Debugging</span></span>](index.md)
