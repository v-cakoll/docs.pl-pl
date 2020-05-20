---
title: 'IXCLRDataMethodDefinition:: EndEnumInstances, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7271c9594a679af205c404f59ff6731821aa0acf
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420997"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="ad1c4-102">IXCLRDataMethodDefinition:: EndEnumInstances, Metoda</span><span class="sxs-lookup"><span data-stu-id="ad1c4-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="ad1c4-103">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ad1c4-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ad1c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad1c4-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="ad1c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad1c4-105">Parameters</span></span>

`handle`\
<span data-ttu-id="ad1c4-106">określoną Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ad1c4-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad1c4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad1c4-107">Remarks</span></span>

<span data-ttu-id="ad1c4-108">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejsu i odpowiada siódmemu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="ad1c4-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad1c4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad1c4-109">Requirements</span></span>

<span data-ttu-id="ad1c4-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad1c4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ad1c4-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ad1c4-111">**Header:** None</span></span>  
<span data-ttu-id="ad1c4-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ad1c4-112">**Library:** None</span></span>  
<span data-ttu-id="ad1c4-113">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ad1c4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad1c4-114">See also</span></span>

- [<span data-ttu-id="ad1c4-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ad1c4-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="ad1c4-116">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad1c4-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
