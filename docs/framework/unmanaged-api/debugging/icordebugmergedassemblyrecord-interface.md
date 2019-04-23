---
title: ICorDebugMergedAssemblyRecord, interfejs
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180469"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="0e1bc-102">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e1bc-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="0e1bc-103">Zawiera informacje o zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e1bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e1bc-104">Methods</span></span>  
  
|<span data-ttu-id="0e1bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e1bc-105">Method</span></span>|<span data-ttu-id="0e1bc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0e1bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e1bc-107">GetCulture, metoda</span><span class="sxs-lookup"><span data-stu-id="0e1bc-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="0e1bc-108">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="0e1bc-109">GetIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="0e1bc-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="0e1bc-110">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="0e1bc-111">GetPublicKey, metoda</span><span class="sxs-lookup"><span data-stu-id="0e1bc-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="0e1bc-112">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="0e1bc-113">GetPublicKeyToken, metoda</span><span class="sxs-lookup"><span data-stu-id="0e1bc-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="0e1bc-114">Pobiera klucz publiczny zestawu token.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="0e1bc-115">GetSimpleName, metoda</span><span class="sxs-lookup"><span data-stu-id="0e1bc-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="0e1bc-116">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="0e1bc-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="0e1bc-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="0e1bc-118">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e1bc-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e1bc-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e1bc-120">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0e1bc-121">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0e1bc-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e1bc-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e1bc-122">Requirements</span></span>  
 <span data-ttu-id="0e1bc-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e1bc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e1bc-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e1bc-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e1bc-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e1bc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e1bc-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e1bc-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1bc-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e1bc-127">See also</span></span>

- [<span data-ttu-id="0e1bc-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0e1bc-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0e1bc-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0e1bc-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
