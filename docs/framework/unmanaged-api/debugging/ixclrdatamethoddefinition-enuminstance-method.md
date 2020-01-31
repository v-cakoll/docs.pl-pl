---
title: 'IXCLRDataMethodDefinition:: EnumInstance, Metoda'
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
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790444"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="8df9a-102">IXCLRDataMethodDefinition:: EnumInstance, Metoda</span><span class="sxs-lookup"><span data-stu-id="8df9a-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="8df9a-103">Wylicza wystąpienia tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="8df9a-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8df9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8df9a-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="8df9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8df9a-105">Parameters</span></span>

`handle`\
<span data-ttu-id="8df9a-106">[in. out] Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8df9a-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="8df9a-107">określoną Wyliczane wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="8df9a-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="8df9a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8df9a-108">Remarks</span></span>

<span data-ttu-id="8df9a-109">Podana metoda jest częścią interfejsu `IXCLRDataMethodDefinition` i odpowiada czwartemu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="8df9a-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="8df9a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8df9a-110">Requirements</span></span>

<span data-ttu-id="8df9a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8df9a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8df9a-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="8df9a-112">**Header:** None</span></span>  
<span data-ttu-id="8df9a-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="8df9a-113">**Library:** None</span></span>  
<span data-ttu-id="8df9a-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8df9a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8df9a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8df9a-115">See also</span></span>

- [<span data-ttu-id="8df9a-116">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8df9a-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="8df9a-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8df9a-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="8df9a-118">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="8df9a-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="8df9a-119">IXCLRDataMethodInstance, interfejs</span><span class="sxs-lookup"><span data-stu-id="8df9a-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
