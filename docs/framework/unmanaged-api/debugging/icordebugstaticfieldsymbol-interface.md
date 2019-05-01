---
title: ICorDebugStaticFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 382f3fc9377c25379809badac0bc580c3593cbde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782593"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="14d56-102">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="14d56-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="14d56-103">Reprezentuje informacji dotyczących symboli debugowania dla pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="14d56-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14d56-104">Metody</span><span class="sxs-lookup"><span data-stu-id="14d56-104">Methods</span></span>  
  
|<span data-ttu-id="14d56-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="14d56-105">Method</span></span>|<span data-ttu-id="14d56-106">Opis</span><span class="sxs-lookup"><span data-stu-id="14d56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14d56-107">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="14d56-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="14d56-108">Pobiera adres pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="14d56-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="14d56-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="14d56-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="14d56-110">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="14d56-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="14d56-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="14d56-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="14d56-112">Pobiera rozmiar w bajtach pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="14d56-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14d56-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14d56-113">Remarks</span></span>  
 <span data-ttu-id="14d56-114">`ICorDebugStaticFieldSymbol` Interfejsu służy do pobierania informacji dotyczących symboli debugowania dla pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="14d56-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14d56-115">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14d56-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="14d56-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="14d56-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14d56-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14d56-117">Requirements</span></span>  
 <span data-ttu-id="14d56-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14d56-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14d56-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14d56-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14d56-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14d56-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14d56-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14d56-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d56-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14d56-122">See also</span></span>

- [<span data-ttu-id="14d56-123">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="14d56-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="14d56-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="14d56-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="14d56-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="14d56-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
