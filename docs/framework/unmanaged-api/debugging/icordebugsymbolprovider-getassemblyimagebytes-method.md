---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes — metoda
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7975ca3da16be10285e618752981249602371c43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418594"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="c3e31-102">ICorDebugSymbolProvider::GetAssemblyImageBytes — metoda</span><span class="sxs-lookup"><span data-stu-id="c3e31-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="c3e31-103">Odczytuje dane z zestawu scalonych podany wirtualny adres względny (RVA) w zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="c3e31-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3e31-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3e31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3e31-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="c3e31-106">[in] Wirtualny adres względny (RVA) w zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="c3e31-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="c3e31-107">Liczba bajtów do odczytu z zestawu scalone.</span><span class="sxs-lookup"><span data-stu-id="c3e31-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="c3e31-108">Wskaźnik do adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiekt, który zawiera informacje o bufora pamięci z metadanych zestawu scalone.</span><span class="sxs-lookup"><span data-stu-id="c3e31-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3e31-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3e31-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3e31-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3e31-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e31-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3e31-111">Requirements</span></span>  
 <span data-ttu-id="c3e31-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3e31-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3e31-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3e31-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3e31-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3e31-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3e31-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3e31-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e31-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3e31-116">See Also</span></span>  
 [<span data-ttu-id="c3e31-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3e31-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="c3e31-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3e31-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
