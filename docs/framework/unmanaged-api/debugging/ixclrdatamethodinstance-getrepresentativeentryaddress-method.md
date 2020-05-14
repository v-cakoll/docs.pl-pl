---
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress, Metoda'
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
ms.openlocfilehash: d9f9e16d243c0f3b45ac24776caea5bb9c32dcc1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395751"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="b75c4-102">IXCLRDataMethodInstance:: GetRepresentativeEntryAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="b75c4-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="b75c4-103">Pobiera najbardziej reprezentatywny adres punktu wejścia dla natywnej kompilacji wszystkich możliwych punktów wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="b75c4-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b75c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b75c4-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="b75c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b75c4-105">Parameters</span></span>

`addr`\
<span data-ttu-id="b75c4-106">określoną Adres najbardziej reprezentatywnego macierzystego punktu wejścia dla metody.</span><span class="sxs-lookup"><span data-stu-id="b75c4-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="b75c4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b75c4-107">Remarks</span></span>

<span data-ttu-id="b75c4-108">Podana metoda jest częścią [ `IXCLRDataMethodInstance` interfejsu](ixclrdatamethodinstance-interface.md) i odpowiada dwudziestemu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="b75c4-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b75c4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b75c4-109">Requirements</span></span>

<span data-ttu-id="b75c4-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b75c4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b75c4-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="b75c4-111">**Header:** None</span></span>  
<span data-ttu-id="b75c4-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="b75c4-112">**Library:** None</span></span>  
<span data-ttu-id="b75c4-113">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b75c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b75c4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b75c4-114">See also</span></span>

- [<span data-ttu-id="b75c4-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b75c4-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="b75c4-116">IXCLRDataMethodInstance, interfejs</span><span class="sxs-lookup"><span data-stu-id="b75c4-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
