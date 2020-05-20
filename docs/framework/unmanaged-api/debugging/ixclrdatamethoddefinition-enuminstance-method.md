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
ms.openlocfilehash: ae1ef2a3c8cf9e042ab9ab233ed993f8e36b2fce
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420945"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="38275-102">IXCLRDataMethodDefinition:: EnumInstance, Metoda</span><span class="sxs-lookup"><span data-stu-id="38275-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="38275-103">Wylicza wystąpienia tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="38275-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="38275-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38275-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="38275-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38275-105">Parameters</span></span>

`handle`\
<span data-ttu-id="38275-106">[in. out] Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="38275-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="38275-107">określoną Wyliczane wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="38275-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="38275-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38275-108">Remarks</span></span>

<span data-ttu-id="38275-109">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejsu i odpowiada szóstemu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="38275-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="38275-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38275-110">Requirements</span></span>

<span data-ttu-id="38275-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38275-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="38275-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="38275-112">**Header:** None</span></span>  
<span data-ttu-id="38275-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="38275-113">**Library:** None</span></span>  
<span data-ttu-id="38275-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="38275-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="38275-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38275-115">See also</span></span>

- [<span data-ttu-id="38275-116">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38275-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="38275-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="38275-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="38275-118">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="38275-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="38275-119">IXCLRDataMethodInstance, interfejs</span><span class="sxs-lookup"><span data-stu-id="38275-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
