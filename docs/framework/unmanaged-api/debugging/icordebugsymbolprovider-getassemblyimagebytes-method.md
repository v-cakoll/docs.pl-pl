---
title: "ICorDebugSymbolProvider::GetAssemblyImageBytes — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23c6dc836aefe1dd89431e003058ba2056eba3ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="1b50c-102">ICorDebugSymbolProvider::GetAssemblyImageBytes — metoda</span><span class="sxs-lookup"><span data-stu-id="1b50c-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="1b50c-103">Odczytuje dane z zestawu scalonych podany wirtualny adres względny (RVA) w zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="1b50c-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b50c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b50c-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b50c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b50c-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="1b50c-106">[in] Wirtualny adres względny (RVA) w zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="1b50c-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="1b50c-107">Liczba bajtów do odczytu z zestawu scalone.</span><span class="sxs-lookup"><span data-stu-id="1b50c-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="1b50c-108">Wskaźnik do adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiekt, który zawiera informacje o bufora pamięci z metadanych zestawu scalone.</span><span class="sxs-lookup"><span data-stu-id="1b50c-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b50c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b50c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b50c-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1b50c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b50c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b50c-111">Requirements</span></span>  
 <span data-ttu-id="1b50c-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b50c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b50c-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b50c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b50c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b50c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b50c-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b50c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b50c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b50c-116">See Also</span></span>  
 [<span data-ttu-id="1b50c-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b50c-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="1b50c-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1b50c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
