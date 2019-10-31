---
title: ICorDebugInstanceFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 2ed1d70f554ca0a4a49639fe53a2ddbb0497c0a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122735"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="b73e7-102">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="b73e7-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="b73e7-103">Przedstawia informacje o symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b73e7-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b73e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b73e7-104">Methods</span></span>  
  
|<span data-ttu-id="b73e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b73e7-105">Method</span></span>|<span data-ttu-id="b73e7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b73e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b73e7-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="b73e7-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="b73e7-108">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b73e7-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="b73e7-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="b73e7-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="b73e7-110">Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="b73e7-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="b73e7-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="b73e7-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="b73e7-112">Pobiera rozmiar w bajtach pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b73e7-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b73e7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b73e7-113">Remarks</span></span>  
 <span data-ttu-id="b73e7-114">Interfejs `ICorDebugInstanceFieldSymbol` służy do pobierania informacji o symbolach debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b73e7-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b73e7-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b73e7-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b73e7-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="b73e7-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b73e7-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b73e7-117">Requirements</span></span>  
 <span data-ttu-id="b73e7-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b73e7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b73e7-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b73e7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b73e7-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b73e7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b73e7-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b73e7-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b73e7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b73e7-122">See also</span></span>

- [<span data-ttu-id="b73e7-123">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="b73e7-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="b73e7-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b73e7-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b73e7-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b73e7-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
