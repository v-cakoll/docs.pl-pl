---
title: 'ICorDebugSymbolProvider:: GetAssemblyImageBytes, Metoda'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: a555acb9e23098b0a0f70924032771b1ae18e88e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376120"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="1c953-102">ICorDebugSymbolProvider:: GetAssemblyImageBytes, Metoda</span><span class="sxs-lookup"><span data-stu-id="1c953-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="1c953-103">Odczytuje dane z scalonego zestawu, uwzględniając względny adres wirtualny (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1c953-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c953-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c953-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c953-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c953-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="1c953-106">podczas Względny adres wirtualny (RVA) w scalonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1c953-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="1c953-107">Liczba bajtów do odczytania ze scalonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1c953-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="1c953-108">Wskaźnik do adresu obiektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) , który zawiera informacje o buforze pamięci ze scalonymi metadanymi zestawu.</span><span class="sxs-lookup"><span data-stu-id="1c953-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c953-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c953-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c953-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1c953-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c953-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c953-111">Requirements</span></span>  
 <span data-ttu-id="1c953-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c953-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c953-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c953-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c953-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c953-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c953-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c953-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c953-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c953-116">See also</span></span>

- [<span data-ttu-id="1c953-117">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c953-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1c953-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1c953-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
