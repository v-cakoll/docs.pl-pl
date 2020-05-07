---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: aebf499d7d25caef80782cc5661a57048dc5f6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894863"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="030de-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="030de-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="030de-103">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="030de-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="030de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="030de-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="030de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="030de-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="030de-106">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugAssemblyEnum, który jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="030de-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="030de-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="030de-107">Return Value</span></span>  
 <span data-ttu-id="030de-108">`S_OK`Jeśli ten `ICorDebugAssembly3` obiekt jest kontenerem; w przeciwnym `S_FALSE`razie, a Wyliczenie jest puste.</span><span class="sxs-lookup"><span data-stu-id="030de-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="030de-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="030de-109">Remarks</span></span>  
 <span data-ttu-id="030de-110">Symbole są konieczne do wyliczenia zawartych zestawów.</span><span class="sxs-lookup"><span data-stu-id="030de-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="030de-111">Jeśli ich nie ma, metoda zwraca `S_FALSE`i nie podano prawidłowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="030de-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="030de-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="030de-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="030de-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="030de-113">Requirements</span></span>  
 <span data-ttu-id="030de-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="030de-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="030de-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="030de-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="030de-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="030de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="030de-117">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="030de-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030de-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="030de-118">See also</span></span>

- [<span data-ttu-id="030de-119">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="030de-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="030de-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="030de-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
