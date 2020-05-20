---
title: 'ISOSDacInterface:: GetMethodDescData, Metoda'
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
ms.openlocfilehash: 105149d0abf312c33a8498e7428e3a8b23d6ae7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421023"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="7bdec-102">ISOSDacInterface:: GetMethodDescData, Metoda</span><span class="sxs-lookup"><span data-stu-id="7bdec-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="7bdec-103">Pobiera dane dla danego wskaźnika MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="7bdec-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7bdec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bdec-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="7bdec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bdec-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="7bdec-106">podczas Adres MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="7bdec-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="7bdec-107">podczas Adres IP metody.</span><span class="sxs-lookup"><span data-stu-id="7bdec-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="7bdec-108">określoną Dane skojarzone z MethodDesc jako zwrócone z wewnętrznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="7bdec-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="7bdec-109">określoną Liczba przywróconych wersji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="7bdec-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="7bdec-110">określoną Dane skojarzone z przywróconymi wersjami ReJIT, które są zwracane z wewnętrznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="7bdec-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="7bdec-111">określoną Liczba bajtów wymagana do przechowywania danych skojarzonych z przywróconymi wersjami ReJit.</span><span class="sxs-lookup"><span data-stu-id="7bdec-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="7bdec-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bdec-112">Remarks</span></span>

<span data-ttu-id="7bdec-113">Podana metoda jest częścią `ISOSDacInterface` interfejsu i odpowiada dwudziestemu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="7bdec-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="7bdec-114">Aby można było ich używać, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) należy zdefiniować jako 64-bitową liczbę całkowitą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="7bdec-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="7bdec-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bdec-115">Requirements</span></span>

<span data-ttu-id="7bdec-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bdec-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7bdec-117">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="7bdec-117">**Header:** None</span></span>  
<span data-ttu-id="7bdec-118">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="7bdec-118">**Library:** None</span></span>  
<span data-ttu-id="7bdec-119">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7bdec-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7bdec-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bdec-120">See also</span></span>

- [<span data-ttu-id="7bdec-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7bdec-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="7bdec-122">ISOSDacInterface, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bdec-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
