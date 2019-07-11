---
title: Metoda IXCLRDataMethodDefinition::EnumInstance
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ad1a9957e9bffd7b28aa241723dedba1d11f4cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775869"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="0f4ae-102">Metoda IXCLRDataMethodDefinition::EnumInstance</span><span class="sxs-lookup"><span data-stu-id="0f4ae-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="0f4ae-103">Wylicza wystąpień tę definicję metody.</span><span class="sxs-lookup"><span data-stu-id="0f4ae-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0f4ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f4ae-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="0f4ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f4ae-105">Parameters</span></span>

`handle`\
<span data-ttu-id="0f4ae-106">[out w] Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0f4ae-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="0f4ae-107">[out] Wystąpienie wyliczany.</span><span class="sxs-lookup"><span data-stu-id="0f4ae-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f4ae-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f4ae-108">Remarks</span></span>

<span data-ttu-id="0f4ae-109">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejs i odpowiada czwarte miejsce tabeli wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="0f4ae-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f4ae-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f4ae-110">Requirements</span></span>

<span data-ttu-id="0f4ae-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f4ae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0f4ae-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="0f4ae-112">**Header:** None</span></span>  
<span data-ttu-id="0f4ae-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="0f4ae-113">**Library:** None</span></span>  
<span data-ttu-id="0f4ae-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f4ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0f4ae-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f4ae-115">See also</span></span>

- [<span data-ttu-id="0f4ae-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="0f4ae-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0f4ae-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0f4ae-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="0f4ae-118">Interfejs IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="0f4ae-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="0f4ae-119">Interfejs IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="0f4ae-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
