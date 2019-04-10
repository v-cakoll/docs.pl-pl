---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bd4cd44eca9b12ab8773fd75b6262579cfe8e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206086"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="cac73-102">Metoda ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="cac73-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="cac73-103">Zwraca zestaw kontenerów to `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="cac73-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cac73-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cac73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cac73-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="cac73-106">Wskaźnik na adres ICorDebugAssembly obiekt, który reprezentuje zestaw kontenerów lub **null** Jeśli wywołanie metody nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="cac73-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cac73-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cac73-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="cac73-108">Jeśli wywołanie metody zakończy się pomyślnie; w przeciwnym razie `S_FALSE`, i `ppAssembly` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="cac73-108">if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cac73-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cac73-109">Remarks</span></span>  
 <span data-ttu-id="cac73-110">Jeśli ten zestaw został połączony z innymi osobami w zestawu pojedynczego kontenera, ta metoda zwraca zestaw kontenerów.</span><span class="sxs-lookup"><span data-stu-id="cac73-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="cac73-111">Aby uzyskać więcej informacji i terminologii, zobacz [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="cac73-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cac73-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cac73-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cac73-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cac73-113">Requirements</span></span>  
 <span data-ttu-id="cac73-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cac73-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cac73-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cac73-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cac73-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cac73-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cac73-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cac73-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cac73-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cac73-118">See also</span></span>

- [<span data-ttu-id="cac73-119">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="cac73-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="cac73-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cac73-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
