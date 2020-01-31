---
title: ICorDebugVariableSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 9d17bc92dcae9e906dfe18d7665fbf489d278234
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790869"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="236ab-102">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="236ab-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="236ab-103">Pobiera informacje o symbolach debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="236ab-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="236ab-104">Metody</span><span class="sxs-lookup"><span data-stu-id="236ab-104">Methods</span></span>  
  
|<span data-ttu-id="236ab-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="236ab-105">Method</span></span>|<span data-ttu-id="236ab-106">Opis</span><span class="sxs-lookup"><span data-stu-id="236ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="236ab-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="236ab-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="236ab-108">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="236ab-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="236ab-109">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="236ab-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="236ab-110">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="236ab-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="236ab-111">GetSlotIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="236ab-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="236ab-112">Pobiera indeks gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="236ab-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="236ab-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="236ab-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="236ab-114">Pobiera wartość zmiennej jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="236ab-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="236ab-115">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="236ab-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="236ab-116">Przypisuje wartość tablicy bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="236ab-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="236ab-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="236ab-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="236ab-118">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="236ab-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="236ab-119">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="236ab-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236ab-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="236ab-120">Requirements</span></span>  
 <span data-ttu-id="236ab-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236ab-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236ab-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="236ab-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="236ab-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="236ab-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="236ab-124">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236ab-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236ab-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="236ab-125">See also</span></span>

- [<span data-ttu-id="236ab-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="236ab-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="236ab-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="236ab-127">Debugging</span></span>](index.md)
