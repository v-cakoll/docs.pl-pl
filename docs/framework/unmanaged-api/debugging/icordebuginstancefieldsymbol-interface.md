---
title: ICorDebugInstanceFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 092f2a8acdffa9f91176bdf0ca10b8db9cff6d37
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209933"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="97c5a-102">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="97c5a-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="97c5a-103">Przedstawia informacje o symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="97c5a-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97c5a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="97c5a-104">Methods</span></span>  
  
|<span data-ttu-id="97c5a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="97c5a-105">Method</span></span>|<span data-ttu-id="97c5a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="97c5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97c5a-107">GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="97c5a-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="97c5a-108">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="97c5a-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="97c5a-109">GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="97c5a-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="97c5a-110">Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="97c5a-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="97c5a-111">GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="97c5a-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="97c5a-112">Pobiera rozmiar w bajtach pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="97c5a-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97c5a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97c5a-113">Remarks</span></span>  
 <span data-ttu-id="97c5a-114">`ICorDebugInstanceFieldSymbol`Interfejs jest używany do pobierania informacji o symbolach debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="97c5a-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97c5a-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="97c5a-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="97c5a-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="97c5a-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97c5a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97c5a-117">Requirements</span></span>  
 <span data-ttu-id="97c5a-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97c5a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97c5a-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97c5a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97c5a-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="97c5a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97c5a-121">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97c5a-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c5a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97c5a-122">See also</span></span>

- [<span data-ttu-id="97c5a-123">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="97c5a-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="97c5a-124">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="97c5a-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="97c5a-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="97c5a-125">Debugging</span></span>](index.md)
