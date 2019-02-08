---
title: Metoda ISOSDacInterface::GetMethodDescData
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 47cea4810b764005e87d00966c15cf138f5913a7
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825956"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="06782-102">Metoda ISOSDacInterface::GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="06782-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="06782-103">Pobiera dane dla danego wskaźnika MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="06782-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="06782-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06782-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="06782-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06782-105">Parameters</span></span>

<span data-ttu-id="06782-106">`methodDesc` [in] Adres MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="06782-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="06782-107">`ip` [in] Adres IP metody.</span><span class="sxs-lookup"><span data-stu-id="06782-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="06782-108">`data` [out] Dane skojarzone z MethodDesc w postaci zwracanej przez wewnętrznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="06782-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

<span data-ttu-id="06782-109">`cRevertedRejitVersions` [out] Numer wersji przywróconym rejit.</span><span class="sxs-lookup"><span data-stu-id="06782-109">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="06782-110">`rgRevertedRejitData` [out] Dane związane z wersjami przywróconym rejit jak zwrócony z wewnętrznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="06782-110">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

<span data-ttu-id="06782-111">`pcNeededRevertedRejitData` [out] Liczba bajtów potrzebnych do przechowania danych skojarzonych z przywróconym wersje ReJit.</span><span class="sxs-lookup"><span data-stu-id="06782-111">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="06782-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06782-112">Remarks</span></span>

<span data-ttu-id="06782-113">Podana metoda jest częścią `ISOSDacInterface` interfejs i odnosi się do 20 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="06782-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="06782-114">Aby móc ich używać, [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) musi być zdefiniowany jako 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="06782-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="06782-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06782-115">Requirements</span></span>

<span data-ttu-id="06782-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06782-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="06782-117">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="06782-117">**Header:** None</span></span>  
<span data-ttu-id="06782-118">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="06782-118">**Library:** None</span></span>  
<span data-ttu-id="06782-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="06782-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="06782-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06782-120">See also</span></span>

- [<span data-ttu-id="06782-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="06782-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="06782-122">Interfejs ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="06782-122">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
