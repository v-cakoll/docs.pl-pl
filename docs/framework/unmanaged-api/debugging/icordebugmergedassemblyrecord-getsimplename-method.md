---
title: 'ICorDebugMergedAssemblyRecord:: getsimplename — Metoda'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3256a1a50b66be74561bfc992380669a4495dde
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939987"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="d4aef-102">ICorDebugMergedAssemblyRecord:: getsimplename — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4aef-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="d4aef-103">Pobiera prostą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="d4aef-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4aef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4aef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4aef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4aef-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d4aef-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="d4aef-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d4aef-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana `szName` w buforze.</span><span class="sxs-lookup"><span data-stu-id="d4aef-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="d4aef-108">Wskaźnik do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="d4aef-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4aef-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4aef-109">Remarks</span></span>  
 <span data-ttu-id="d4aef-110">Ta metoda pobiera prostą nazwę zestawu (na przykład "System. Collections") bez rozszerzenia pliku, wersji, kultury lub tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="d4aef-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="d4aef-111">Odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d4aef-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4aef-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d4aef-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4aef-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4aef-113">Requirements</span></span>  
 <span data-ttu-id="d4aef-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4aef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4aef-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4aef-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4aef-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4aef-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4aef-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4aef-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4aef-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4aef-118">See also</span></span>

- [<span data-ttu-id="d4aef-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4aef-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="d4aef-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d4aef-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
