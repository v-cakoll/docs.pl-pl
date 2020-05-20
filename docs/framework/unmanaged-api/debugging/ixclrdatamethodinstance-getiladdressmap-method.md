---
title: 'IXCLRDataMethodInstance:: GetILAddressMap, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0acfa9ffd6f4bc3be567855008dccd08c9c74153
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420919"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="6639a-102">IXCLRDataMethodInstance:: GetILAddressMap, Metoda</span><span class="sxs-lookup"><span data-stu-id="6639a-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="6639a-103">Pobiera informacje o mapowaniu IL to Address.</span><span class="sxs-lookup"><span data-stu-id="6639a-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6639a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6639a-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="6639a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6639a-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="6639a-106">podczas Długość dostarczonej tablicy map.</span><span class="sxs-lookup"><span data-stu-id="6639a-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="6639a-107">określoną Liczba wpisów mapowania wymaganych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="6639a-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="6639a-108">[out, size_is (mapLen)] Tablica do przechowywania wpisów mapy.</span><span class="sxs-lookup"><span data-stu-id="6639a-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="6639a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6639a-109">Remarks</span></span>

<span data-ttu-id="6639a-110">Podana metoda jest częścią `IXCLRDataMethodInstance` interfejsu i odpowiada 15emu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6639a-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6639a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6639a-111">Requirements</span></span>

<span data-ttu-id="6639a-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6639a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6639a-113">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="6639a-113">**Header:** None</span></span>  
<span data-ttu-id="6639a-114">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="6639a-114">**Library:** None</span></span>  
<span data-ttu-id="6639a-115">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6639a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6639a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6639a-116">See also</span></span>

- [<span data-ttu-id="6639a-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6639a-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="6639a-118">IXCLRDataMethodInstance, interfejs</span><span class="sxs-lookup"><span data-stu-id="6639a-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
