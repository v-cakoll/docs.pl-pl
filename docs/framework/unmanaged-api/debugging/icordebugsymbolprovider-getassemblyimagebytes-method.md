---
title: ICorDebugSymbolProvider::Metoda GetAssemblyImageBytes
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178494"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="7cec5-102">ICorDebugSymbolProvider::Metoda GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="7cec5-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="7cec5-103">Odczytuje dane z scalonego zestawu o względnym adresie wirtualnym (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="7cec5-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cec5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cec5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cec5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cec5-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="7cec5-106">[w] Względny adres wirtualny (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="7cec5-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="7cec5-107">Liczba bajtów do odczytania z scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7cec5-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="7cec5-108">Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer,](icordebugmemorybuffer-interface.md) który zawiera informacje o buforze pamięci z scalonymi metadanymi zestawu.</span><span class="sxs-lookup"><span data-stu-id="7cec5-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cec5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cec5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cec5-110">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7cec5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cec5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cec5-111">Requirements</span></span>  
 <span data-ttu-id="7cec5-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cec5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cec5-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cec5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cec5-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cec5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cec5-115">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cec5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cec5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cec5-116">See also</span></span>

- [<span data-ttu-id="7cec5-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="7cec5-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="7cec5-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7cec5-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
