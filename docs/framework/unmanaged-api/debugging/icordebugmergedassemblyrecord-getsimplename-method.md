---
title: ICorDebugMergedAssemblyRecord::Metoda GetSimpleName
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178706"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="3dec5-102">ICorDebugMergedAssemblyRecord::Metoda GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="3dec5-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="3dec5-103">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="3dec5-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dec5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3dec5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dec5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dec5-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3dec5-106">[w] Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="3dec5-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3dec5-107">[na zewnątrz] Wskaźnik do liczby znaków faktycznie zapisane `szName` w buforze.</span><span class="sxs-lookup"><span data-stu-id="3dec5-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="3dec5-108">Wskaźnik do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="3dec5-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dec5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dec5-109">Remarks</span></span>  
 <span data-ttu-id="3dec5-110">Ta metoda pobiera prostą nazwę zestawu (na przykład "System.Collections"), bez rozszerzenia pliku, wersji, kultury lub tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3dec5-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="3dec5-111">Odpowiada właściwości w <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3dec5-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dec5-112">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3dec5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dec5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3dec5-113">Requirements</span></span>  
 <span data-ttu-id="3dec5-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dec5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dec5-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dec5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dec5-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dec5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dec5-117">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dec5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dec5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dec5-118">See also</span></span>

- [<span data-ttu-id="3dec5-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="3dec5-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="3dec5-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3dec5-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
