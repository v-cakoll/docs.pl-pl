---
title: ICorDebugInstanceFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777525"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="4b176-102">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b176-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="4b176-103">Przedstawia informacje o symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4b176-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b176-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4b176-104">Methods</span></span>  
  
|<span data-ttu-id="4b176-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b176-105">Method</span></span>|<span data-ttu-id="4b176-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4b176-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b176-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="4b176-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="4b176-108">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4b176-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="4b176-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="4b176-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="4b176-110">Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4b176-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="4b176-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="4b176-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="4b176-112">Pobiera rozmiar w bajtach pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4b176-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b176-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b176-113">Remarks</span></span>  
 <span data-ttu-id="4b176-114">Interfejs `ICorDebugInstanceFieldSymbol` służy do pobierania informacji o symbolach debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4b176-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b176-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4b176-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4b176-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="4b176-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b176-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b176-117">Requirements</span></span>  
 <span data-ttu-id="4b176-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b176-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b176-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b176-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b176-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4b176-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b176-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b176-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b176-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b176-122">See also</span></span>

- [<span data-ttu-id="4b176-123">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b176-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="4b176-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4b176-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4b176-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4b176-125">Debugging</span></span>](index.md)
