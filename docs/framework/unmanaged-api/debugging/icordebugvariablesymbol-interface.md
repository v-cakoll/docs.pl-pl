---
title: ICorDebugVariableSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c7cdababd1e4b5fae4f5e48a654f861b708a6e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226563"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="8b636-102">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b636-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="8b636-103">Umożliwia pobranie informacji dotyczących symboli debugowania dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8b636-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b636-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8b636-104">Methods</span></span>  
  
|<span data-ttu-id="8b636-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b636-105">Method</span></span>|<span data-ttu-id="8b636-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8b636-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b636-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="8b636-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="8b636-108">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8b636-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="8b636-109">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="8b636-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="8b636-110">Pobiera rozmiar zmiennej elementu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8b636-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="8b636-111">GetSlotIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="8b636-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="8b636-112">Pobiera indeks zarządzane miejsce zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="8b636-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="8b636-113">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="8b636-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="8b636-114">Pobiera wartość zmiennej w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="8b636-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="8b636-115">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="8b636-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="8b636-116">Wartość tablicy bajtowej jest przypisywany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8b636-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b636-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b636-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b636-118">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8b636-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8b636-119">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="8b636-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b636-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b636-120">Requirements</span></span>  
 <span data-ttu-id="8b636-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b636-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b636-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b636-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b636-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b636-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8b636-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8b636-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b636-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b636-125">See also</span></span>

- [<span data-ttu-id="8b636-126">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8b636-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8b636-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8b636-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
