---
title: ICorDebugMergedAssemblyRecord, interfejs
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765417"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="a5dc5-102">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5dc5-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="a5dc5-103">Zawiera informacje o zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5dc5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a5dc5-104">Methods</span></span>  
  
|<span data-ttu-id="a5dc5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a5dc5-105">Method</span></span>|<span data-ttu-id="a5dc5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a5dc5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5dc5-107">GetCulture, metoda</span><span class="sxs-lookup"><span data-stu-id="a5dc5-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="a5dc5-108">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="a5dc5-109">GetIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="a5dc5-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="a5dc5-110">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="a5dc5-111">GetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="a5dc5-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="a5dc5-112">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="a5dc5-113">GetPublicKeyToken, metoda</span><span class="sxs-lookup"><span data-stu-id="a5dc5-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="a5dc5-114">Pobiera klucz publiczny zestawu token.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="a5dc5-115">GetSimpleName, metoda</span><span class="sxs-lookup"><span data-stu-id="a5dc5-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="a5dc5-116">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="a5dc5-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="a5dc5-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="a5dc5-118">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5dc5-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5dc5-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5dc5-120">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a5dc5-121">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5dc5-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5dc5-122">Requirements</span></span>  
 <span data-ttu-id="a5dc5-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5dc5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5dc5-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5dc5-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5dc5-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5dc5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5dc5-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5dc5-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5dc5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5dc5-127">See also</span></span>

- [<span data-ttu-id="a5dc5-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a5dc5-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a5dc5-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a5dc5-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
