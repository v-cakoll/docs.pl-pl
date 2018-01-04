---
title: Interfejs ICorDebugSymbolProvider2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7666b8d64b689d3640594f07614be97b72e85a8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="e2024-102">Interfejs ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="e2024-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="e2024-103">Rozszerza logicznie [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji o symbolach dodatkowe debugowania.</span><span class="sxs-lookup"><span data-stu-id="e2024-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2024-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2024-104">Methods</span></span>  
  
|<span data-ttu-id="e2024-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2024-105">Method</span></span>|<span data-ttu-id="e2024-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e2024-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2024-107">GetFrameProps, metoda</span><span class="sxs-lookup"><span data-stu-id="e2024-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="e2024-108">Zwraca metodę uruchamiania wirtualny adres względny metody i ramka nadrzędny podany wirtualny adres względny kodu.</span><span class="sxs-lookup"><span data-stu-id="e2024-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="e2024-109">GetGenericDictionaryInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="e2024-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="e2024-110">Pobiera mapy ogólnego słownika.</span><span class="sxs-lookup"><span data-stu-id="e2024-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2024-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2024-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2024-112">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e2024-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e2024-113">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="e2024-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2024-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2024-114">Requirements</span></span>  
 <span data-ttu-id="e2024-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2024-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2024-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2024-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2024-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2024-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2024-118">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2024-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2024-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2024-119">See Also</span></span>  
 [<span data-ttu-id="e2024-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2024-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="e2024-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e2024-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e2024-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e2024-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
