---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080959"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="e44ec-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="e44ec-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="e44ec-103">Pobiera moduł wyliczający dla zestawów znajdujących się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="e44ec-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e44ec-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e44ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e44ec-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="e44ec-106">[out] Wskaźnik na adres icordebugassemblyenum — interfejs obiekt modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="e44ec-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e44ec-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e44ec-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="e44ec-108">Jeśli ten `ICorDebugAssembly3` obiekt to kontener, a w przeciwnym razie `S_FALSE`, i wyliczenia jest pusty.</span><span class="sxs-lookup"><span data-stu-id="e44ec-108">if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e44ec-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e44ec-109">Remarks</span></span>  
 <span data-ttu-id="e44ec-110">Symbole są wymagane do wyliczenia zawarte zestawów.</span><span class="sxs-lookup"><span data-stu-id="e44ec-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="e44ec-111">Jeśli nie są obecne, metoda zwraca `S_FALSE`, i jest dostępne nie prawidłowym modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="e44ec-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e44ec-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e44ec-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e44ec-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e44ec-113">Requirements</span></span>  
 <span data-ttu-id="e44ec-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e44ec-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e44ec-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e44ec-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e44ec-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e44ec-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e44ec-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e44ec-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e44ec-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e44ec-118">See also</span></span>

- [<span data-ttu-id="e44ec-119">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="e44ec-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="e44ec-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e44ec-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
