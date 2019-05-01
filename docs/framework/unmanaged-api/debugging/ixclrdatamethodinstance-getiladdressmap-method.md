---
title: Metoda IXCLRDataMethodInstance::GetILAddressMap
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
ms.openlocfilehash: e88897342bf18111ebd4914948ab45085c35ea08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942366"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="1071d-102">Metoda IXCLRDataMethodInstance::GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="1071d-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="1071d-103">Pobiera IL, aby informacje dotyczące mapowania adresu.</span><span class="sxs-lookup"><span data-stu-id="1071d-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1071d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1071d-104">Syntax</span></span>

```
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="1071d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1071d-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="1071d-106">[in] Długość tablicy podana mapy.</span><span class="sxs-lookup"><span data-stu-id="1071d-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="1071d-107">[out] Liczba wpisów map, wymaganych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="1071d-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="1071d-108">[out, size_is(mapLen)] Tablica do przechowywania wpisów map.</span><span class="sxs-lookup"><span data-stu-id="1071d-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="1071d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1071d-109">Remarks</span></span>

<span data-ttu-id="1071d-110">Podana metoda jest częścią `IXCLRDataMethodInstance` interfejs i odnosi się do 14 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="1071d-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1071d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1071d-111">Requirements</span></span>

<span data-ttu-id="1071d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1071d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1071d-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="1071d-113">**Header:** None</span></span>  
<span data-ttu-id="1071d-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="1071d-114">**Library:** None</span></span>  
<span data-ttu-id="1071d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1071d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1071d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1071d-116">See also</span></span>

- [<span data-ttu-id="1071d-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1071d-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="1071d-118">Interfejs IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="1071d-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
