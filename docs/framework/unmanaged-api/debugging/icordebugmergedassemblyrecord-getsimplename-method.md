---
title: ICorDebugMergedAssemblyRecord::GetSimpleName Method
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0919f0cfd0ae1617d140eadd12aa8874c73d8bb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491653"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="5981c-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span><span class="sxs-lookup"><span data-stu-id="5981c-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="5981c-103">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="5981c-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5981c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5981c-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5981c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5981c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5981c-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="5981c-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5981c-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="5981c-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5981c-108">Wskaźnik do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="5981c-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5981c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5981c-109">Remarks</span></span>  
 <span data-ttu-id="5981c-110">Ta metoda pobiera prostą nazwę zestawu (na przykład "System.Collections"), bez rozszerzenia pliku, wersji, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="5981c-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="5981c-111">Odnosi się do <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="5981c-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5981c-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5981c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5981c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5981c-113">Requirements</span></span>  
 <span data-ttu-id="5981c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5981c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5981c-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5981c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5981c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5981c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5981c-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5981c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5981c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5981c-118">See also</span></span>
- [<span data-ttu-id="5981c-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="5981c-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="5981c-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5981c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
