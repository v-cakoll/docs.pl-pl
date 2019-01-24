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
ms.openlocfilehash: 8442d1373ede241d262ab41928fd5d9924ec9c80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567194"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="02a16-102">Metoda IXCLRDataMethodInstance::GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="02a16-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="02a16-103">Pobiera IL, aby informacje dotyczące mapowania adresu.</span><span class="sxs-lookup"><span data-stu-id="02a16-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="02a16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02a16-104">Syntax</span></span>

```
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

### <a name="parameters"></a><span data-ttu-id="02a16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02a16-105">Parameters</span></span>

<span data-ttu-id="02a16-106">`mapLen` [in] Długość tablicy podana mapy.</span><span class="sxs-lookup"><span data-stu-id="02a16-106">`mapLen` [in] The length of the provided maps array.</span></span>

<span data-ttu-id="02a16-107">`mapNeeded` [out] Liczba wpisów map, wymaganych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="02a16-107">`mapNeeded` [out] The number of map entries that the method needs.</span></span>

<span data-ttu-id="02a16-108">`maps` [out, size_is(mapLen)] Tablica do przechowywania wpisów map.</span><span class="sxs-lookup"><span data-stu-id="02a16-108">`maps` [out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="02a16-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02a16-109">Remarks</span></span>

<span data-ttu-id="02a16-110">Podana metoda jest częścią `IXCLRDataMethodInstance` interfejs i odnosi się do 14 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="02a16-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="02a16-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02a16-111">Requirements</span></span>

<span data-ttu-id="02a16-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02a16-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="02a16-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="02a16-113">**Header:** None</span></span>  
<span data-ttu-id="02a16-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="02a16-114">**Library:** None</span></span>  
<span data-ttu-id="02a16-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="02a16-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="02a16-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02a16-116">See also</span></span>

- [<span data-ttu-id="02a16-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="02a16-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="02a16-118">Interfejs IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="02a16-118">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
