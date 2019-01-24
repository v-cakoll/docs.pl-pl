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
ms.openlocfilehash: e56f837c4d3362ec6e71030e4fb475df42b9fba4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639961"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="5f115-102">Metoda ISOSDacInterface::GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="5f115-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="5f115-103">Pobiera dane dla danego [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="5f115-103">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5f115-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f115-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="5f115-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f115-105">Parameters</span></span>

<span data-ttu-id="5f115-106">`methodDesc` [in] Adres MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="5f115-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="5f115-107">`ip` [in] Adres IP metody.</span><span class="sxs-lookup"><span data-stu-id="5f115-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="5f115-108">`data` [out] Dane skojarzone z MethodDesc w postaci zwracanej przez wewnętrznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="5f115-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span> <span data-ttu-id="5f115-109">Struktura wymaga co najmniej 168 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5f115-109">The structure needs at least 168 bytes.</span></span>

<span data-ttu-id="5f115-110">`cRevertedRejitVersions` [out] Numer wersji przywróconym rejit.</span><span class="sxs-lookup"><span data-stu-id="5f115-110">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="5f115-111">`rgRevertedRejitData` [out] Dane związane z wersjami przywróconym rejit jak zwrócony z wewnętrznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="5f115-111">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span> <span data-ttu-id="5f115-112">Struktura wymaga co najmniej 24 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5f115-112">The structure needs at least 24 bytes.</span></span>

<span data-ttu-id="5f115-113">`pcNeededRevertedRejitData` [out] Liczba bajtów potrzebnych do przechowania danych skojarzonych z przywróconym wersje ReJit.</span><span class="sxs-lookup"><span data-stu-id="5f115-113">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f115-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f115-114">Remarks</span></span>

<span data-ttu-id="5f115-115">Podana metoda jest częścią `ISOSDacInterface` interfejs i odnosi się do 20 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="5f115-115">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="5f115-116">Również `CLRDATA_ADDRESS` są 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="5f115-116">Also the `CLRDATA_ADDRESS` are 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f115-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f115-117">Requirements</span></span>

<span data-ttu-id="5f115-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f115-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5f115-119">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="5f115-119">**Header:** None</span></span>  
<span data-ttu-id="5f115-120">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="5f115-120">**Library:** None</span></span>  
<span data-ttu-id="5f115-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5f115-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5f115-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f115-122">See also</span></span>

- [<span data-ttu-id="5f115-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5f115-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="5f115-124">Interfejs ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="5f115-124">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
