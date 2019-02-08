---
title: IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 52b2fdaaefd16a49300641f44041b8352141385b
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828553"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="e8979-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span><span class="sxs-lookup"><span data-stu-id="e8979-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="e8979-103">Pobiera najbardziej reprezentatywnej adres punktu wejścia dla natywnej kompilacji wszystkie możliwe punkty wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="e8979-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e8979-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8979-104">Syntax</span></span>

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

### <a name="parameters"></a><span data-ttu-id="e8979-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8979-105">Parameters</span></span>

<span data-ttu-id="e8979-106">`addr` [out] Adres najbardziej reprezentatywnej natywnego punktu wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="e8979-106">`addr` [out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8979-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8979-107">Remarks</span></span>

<span data-ttu-id="e8979-108">Podana metoda jest częścią [ `IXCLRDataMethodInstance` interfejsu](ixclrdatamethodinstance-interface.md) i odpowiada 19 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="e8979-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 19th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8979-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8979-109">Requirements</span></span>

<span data-ttu-id="e8979-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8979-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e8979-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="e8979-111">**Header:** None</span></span>  
<span data-ttu-id="e8979-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="e8979-112">**Library:** None</span></span>  
<span data-ttu-id="e8979-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e8979-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e8979-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8979-114">See also</span></span>

- [<span data-ttu-id="e8979-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e8979-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e8979-116">Interfejs IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="e8979-116">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
