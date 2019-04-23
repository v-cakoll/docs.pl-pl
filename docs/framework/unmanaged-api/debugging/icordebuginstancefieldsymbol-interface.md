---
title: ICorDebugInstanceFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5c0759989e069169c7e68b71206d9a50b04ad63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111491"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="27380-102">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="27380-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="27380-103">Reprezentuje informacji dotyczących symboli debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="27380-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27380-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27380-104">Methods</span></span>  
  
|<span data-ttu-id="27380-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27380-105">Method</span></span>|<span data-ttu-id="27380-106">Opis</span><span class="sxs-lookup"><span data-stu-id="27380-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27380-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="27380-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="27380-108">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="27380-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="27380-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="27380-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="27380-110">Pobiera przesunięcie w bajtach tego pola wystąpienia w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="27380-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="27380-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="27380-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="27380-112">Pobiera rozmiar w bajtach pole wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="27380-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27380-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27380-113">Remarks</span></span>  
 <span data-ttu-id="27380-114">`ICorDebugInstanceFieldSymbol` Interfejsu służy do pobierania informacji dotyczących symboli debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="27380-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27380-115">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="27380-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="27380-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="27380-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27380-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27380-117">Requirements</span></span>  
 <span data-ttu-id="27380-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27380-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27380-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27380-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27380-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27380-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27380-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27380-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27380-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27380-122">See also</span></span>

- [<span data-ttu-id="27380-123">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="27380-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="27380-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="27380-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="27380-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="27380-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
