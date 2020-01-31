---
title: 'ICorDebugSymbolProvider:: GetObjectSize —, Metoda'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: fce7410b5ae9571af0c8a5963596e2af41737798
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791571"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="f4a40-102">ICorDebugSymbolProvider:: GetObjectSize —, Metoda</span><span class="sxs-lookup"><span data-stu-id="f4a40-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="f4a40-103">Zwraca rozmiar obiektu na podstawie jego podpisu elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="f4a40-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4a40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4a40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4a40-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="f4a40-106">podczas Liczba bajtów w sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="f4a40-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="f4a40-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="f4a40-107">typeSig</span></span>  
 <span data-ttu-id="f4a40-108">podczas Sygnatura elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="f4a40-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="f4a40-109">określoną Wskaźnik do rozmiaru obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4a40-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4a40-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4a40-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4a40-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f4a40-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4a40-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4a40-112">Requirements</span></span>  
 <span data-ttu-id="f4a40-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4a40-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4a40-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f4a40-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4a40-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f4a40-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4a40-116">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4a40-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a40-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4a40-117">See also</span></span>

- [<span data-ttu-id="f4a40-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4a40-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f4a40-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f4a40-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
