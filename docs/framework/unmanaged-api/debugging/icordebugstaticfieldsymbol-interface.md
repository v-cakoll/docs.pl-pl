---
title: ICorDebugStaticFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791805"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="eca0d-102">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="eca0d-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="eca0d-103">Przedstawia informacje o symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="eca0d-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eca0d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eca0d-104">Methods</span></span>  
  
|<span data-ttu-id="eca0d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eca0d-105">Method</span></span>|<span data-ttu-id="eca0d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="eca0d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eca0d-107">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="eca0d-107">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="eca0d-108">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="eca0d-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="eca0d-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="eca0d-109">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="eca0d-110">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="eca0d-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="eca0d-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="eca0d-111">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="eca0d-112">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="eca0d-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eca0d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eca0d-113">Remarks</span></span>  
 <span data-ttu-id="eca0d-114">Interfejs `ICorDebugStaticFieldSymbol` służy do pobierania informacji o symbolach debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="eca0d-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eca0d-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="eca0d-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="eca0d-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="eca0d-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca0d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eca0d-117">Requirements</span></span>  
 <span data-ttu-id="eca0d-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca0d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca0d-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eca0d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eca0d-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eca0d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eca0d-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca0d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca0d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eca0d-122">See also</span></span>

- [<span data-ttu-id="eca0d-123">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="eca0d-123">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="eca0d-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="eca0d-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="eca0d-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="eca0d-125">Debugging</span></span>](index.md)
