---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes Method
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c44260d3b5baa18bc24f85cdbea94016b43291e2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489790"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="f2040-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span><span class="sxs-lookup"><span data-stu-id="f2040-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="f2040-103">Odczytuje dane z zestawu scalonych podane względnych adresów wirtualnych (RVA) w zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="f2040-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2040-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2040-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2040-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2040-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="f2040-106">[in] Względny adres wirtualny (RVA) w zestawie scalone.</span><span class="sxs-lookup"><span data-stu-id="f2040-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="f2040-107">Liczba bajtów do odczytania z zestawu scalonych.</span><span class="sxs-lookup"><span data-stu-id="f2040-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="f2040-108">Wskaźnik na adres [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obiektu, który zawiera informacje o wartość bufora pamięci z metadanych zestawu scalonych.</span><span class="sxs-lookup"><span data-stu-id="f2040-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2040-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2040-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2040-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f2040-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2040-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2040-111">Requirements</span></span>  
 <span data-ttu-id="f2040-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2040-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2040-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2040-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2040-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2040-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2040-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2040-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2040-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2040-116">See also</span></span>
- [<span data-ttu-id="f2040-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2040-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f2040-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f2040-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
