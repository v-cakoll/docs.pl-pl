---
title: Interfejs ICorDebugMergedAssemblyRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 301d7d3d20b78e833101de1df8fd5c271a757144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="900a2-102">Interfejs ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="900a2-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="900a2-103">Zawiera informacje o zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="900a2-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="900a2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="900a2-104">Methods</span></span>  
  
|<span data-ttu-id="900a2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="900a2-105">Method</span></span>|<span data-ttu-id="900a2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="900a2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="900a2-107">GetCulture — metoda</span><span class="sxs-lookup"><span data-stu-id="900a2-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="900a2-108">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="900a2-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="900a2-109">GetIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="900a2-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="900a2-110">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="900a2-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="900a2-111">GetPublicKey — metoda</span><span class="sxs-lookup"><span data-stu-id="900a2-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="900a2-112">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="900a2-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="900a2-113">GetPublicKeyToken — metoda</span><span class="sxs-lookup"><span data-stu-id="900a2-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="900a2-114">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="900a2-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="900a2-115">GetSimpleName — metoda</span><span class="sxs-lookup"><span data-stu-id="900a2-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="900a2-116">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="900a2-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="900a2-117">GetVersion — metoda</span><span class="sxs-lookup"><span data-stu-id="900a2-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="900a2-118">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="900a2-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="900a2-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="900a2-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="900a2-120">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="900a2-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="900a2-121">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="900a2-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="900a2-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="900a2-122">Requirements</span></span>  
 <span data-ttu-id="900a2-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="900a2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="900a2-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="900a2-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="900a2-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="900a2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="900a2-126">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="900a2-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="900a2-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="900a2-127">See Also</span></span>  
 [<span data-ttu-id="900a2-128">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="900a2-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="900a2-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="900a2-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
