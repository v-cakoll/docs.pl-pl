---
title: "ICorDebugMergedAssemblyRecord::GetSimpleName — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 085ca56b3a839689ea38459057957faa81d1dfc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="51ef1-102">ICorDebugMergedAssemblyRecord::GetSimpleName — metoda</span><span class="sxs-lookup"><span data-stu-id="51ef1-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="51ef1-103">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="51ef1-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ef1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51ef1-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51ef1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51ef1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="51ef1-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="51ef1-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="51ef1-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="51ef1-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="51ef1-108">Wskaźnik do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="51ef1-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51ef1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51ef1-109">Remarks</span></span>  
 <span data-ttu-id="51ef1-110">Ta metoda pobiera prostą nazwę zestawu (na przykład "System.Collections"), bez konieczności rozszerzenie pliku, wersji, kultury i tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="51ef1-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="51ef1-111">Odpowiadający mu <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="51ef1-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51ef1-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="51ef1-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ef1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51ef1-113">Requirements</span></span>  
 <span data-ttu-id="51ef1-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51ef1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ef1-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51ef1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51ef1-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51ef1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51ef1-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51ef1-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ef1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51ef1-118">See Also</span></span>  
 [<span data-ttu-id="51ef1-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="51ef1-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="51ef1-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="51ef1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
