---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageBytes, Metoda'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6e707b6176ccd205785aafa6c5a1adf0a3fc78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964665"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="9311d-102">ICorDebugSymbolProvider:: GetAssemblyImageBytes, Metoda</span><span class="sxs-lookup"><span data-stu-id="9311d-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="9311d-103">Odczytuje dane z scalonego zestawu, uwzględniając względny adres wirtualny (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="9311d-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9311d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9311d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9311d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9311d-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="9311d-106">podczas Względny adres wirtualny (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="9311d-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="9311d-107">Liczba bajtów do odczytania ze scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9311d-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="9311d-108">Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) , który zawiera informacje o buforze pamięci ze scalonymi metadanymi zestawu.</span><span class="sxs-lookup"><span data-stu-id="9311d-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9311d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9311d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9311d-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9311d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9311d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9311d-111">Requirements</span></span>  
 <span data-ttu-id="9311d-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9311d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9311d-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9311d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9311d-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9311d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9311d-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9311d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9311d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9311d-116">See also</span></span>

- [<span data-ttu-id="9311d-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="9311d-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9311d-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9311d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
