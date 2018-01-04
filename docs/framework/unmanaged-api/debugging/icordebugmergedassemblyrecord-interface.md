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
ms.workload: dotnet
ms.openlocfilehash: 6086d1a82b5f086d857ac612a9d454a6ed77ba1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="358dc-102">Interfejs ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="358dc-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="358dc-103">Zawiera informacje o zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="358dc-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="358dc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="358dc-104">Methods</span></span>  
  
|<span data-ttu-id="358dc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="358dc-105">Method</span></span>|<span data-ttu-id="358dc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="358dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="358dc-107">GetCulture, metoda</span><span class="sxs-lookup"><span data-stu-id="358dc-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="358dc-108">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="358dc-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="358dc-109">GetIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="358dc-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="358dc-110">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="358dc-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="358dc-111">GetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="358dc-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="358dc-112">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="358dc-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="358dc-113">GetPublicKeyToken, metoda</span><span class="sxs-lookup"><span data-stu-id="358dc-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="358dc-114">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="358dc-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="358dc-115">GetSimpleName, metoda</span><span class="sxs-lookup"><span data-stu-id="358dc-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="358dc-116">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="358dc-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="358dc-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="358dc-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="358dc-118">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="358dc-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="358dc-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="358dc-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="358dc-120">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="358dc-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="358dc-121">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="358dc-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="358dc-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="358dc-122">Requirements</span></span>  
 <span data-ttu-id="358dc-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="358dc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="358dc-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="358dc-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="358dc-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="358dc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="358dc-126">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="358dc-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358dc-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="358dc-127">See Also</span></span>  
 [<span data-ttu-id="358dc-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="358dc-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="358dc-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="358dc-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
