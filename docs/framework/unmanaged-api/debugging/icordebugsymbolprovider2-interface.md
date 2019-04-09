---
title: ICorDebugSymbolProvider2, interfejs
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b787302902779695c48df6e02e2ee00b28f44cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142470"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="bb451-102">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb451-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="bb451-103">Rozszerza logicznie [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji dotyczących symboli debugowania dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="bb451-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb451-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bb451-104">Methods</span></span>  
  
|<span data-ttu-id="bb451-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bb451-105">Method</span></span>|<span data-ttu-id="bb451-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bb451-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb451-107">GetFrameProps, metoda</span><span class="sxs-lookup"><span data-stu-id="bb451-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="bb451-108">Zwraca metodę uruchamiania względny adres wirtualny, metody i podany kod względny adres wirtualny nadrzędnej ramki.</span><span class="sxs-lookup"><span data-stu-id="bb451-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="bb451-109">GetGenericDictionaryInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="bb451-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="bb451-110">Pobiera mapę generyczny słownik.</span><span class="sxs-lookup"><span data-stu-id="bb451-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb451-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb451-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb451-112">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bb451-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="bb451-113">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="bb451-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb451-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb451-114">Requirements</span></span>  
 <span data-ttu-id="bb451-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb451-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb451-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb451-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb451-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb451-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bb451-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bb451-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb451-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb451-119">See also</span></span>

- [<span data-ttu-id="bb451-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb451-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="bb451-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="bb451-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bb451-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bb451-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
