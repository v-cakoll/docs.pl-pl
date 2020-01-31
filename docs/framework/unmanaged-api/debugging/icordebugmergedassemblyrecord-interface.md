---
title: ICorDebugMergedAssemblyRecord, interfejs
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793068"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="c93fe-102">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="c93fe-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="c93fe-103">Zawiera informacje o scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="c93fe-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c93fe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c93fe-104">Methods</span></span>  
  
|<span data-ttu-id="c93fe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c93fe-105">Method</span></span>|<span data-ttu-id="c93fe-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c93fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c93fe-107">GetCulture, metoda</span><span class="sxs-lookup"><span data-stu-id="c93fe-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="c93fe-108">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="c93fe-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="c93fe-109">GetIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="c93fe-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="c93fe-110">Pobiera indeks prefiksu zestawu.</span><span class="sxs-lookup"><span data-stu-id="c93fe-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="c93fe-111">GetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="c93fe-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="c93fe-112">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="c93fe-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="c93fe-113">GetPublicKeyToken, metoda</span><span class="sxs-lookup"><span data-stu-id="c93fe-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="c93fe-114">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c93fe-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="c93fe-115">GetSimpleName, metoda</span><span class="sxs-lookup"><span data-stu-id="c93fe-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="c93fe-116">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="c93fe-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="c93fe-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="c93fe-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="c93fe-118">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="c93fe-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c93fe-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c93fe-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c93fe-120">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c93fe-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c93fe-121">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="c93fe-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c93fe-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c93fe-122">Requirements</span></span>  
 <span data-ttu-id="c93fe-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c93fe-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c93fe-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c93fe-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c93fe-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c93fe-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c93fe-126">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c93fe-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c93fe-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c93fe-127">See also</span></span>

- [<span data-ttu-id="c93fe-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c93fe-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c93fe-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c93fe-129">Debugging</span></span>](index.md)
