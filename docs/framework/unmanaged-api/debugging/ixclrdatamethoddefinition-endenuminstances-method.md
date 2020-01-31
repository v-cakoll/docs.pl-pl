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
ms.openlocfilehash: 605a4244d20ef6c0b7af3c2b26b65ff2a63fa9dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790447"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="9469d-102">IXCLRDataMethodDefinition:: EndEnumInstances, Metoda</span><span class="sxs-lookup"><span data-stu-id="9469d-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="9469d-103">Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9469d-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9469d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9469d-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="9469d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9469d-105">Parameters</span></span>

`handle`\
<span data-ttu-id="9469d-106">określoną Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9469d-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="9469d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9469d-107">Remarks</span></span>

<span data-ttu-id="9469d-108">Podana metoda jest częścią interfejsu `IXCLRDataMethodDefinition` i odpowiada piątemu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="9469d-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9469d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9469d-109">Requirements</span></span>

<span data-ttu-id="9469d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9469d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9469d-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="9469d-111">**Header:** None</span></span>  
<span data-ttu-id="9469d-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="9469d-112">**Library:** None</span></span>  
<span data-ttu-id="9469d-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9469d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9469d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9469d-114">See also</span></span>

- [<span data-ttu-id="9469d-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9469d-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="9469d-116">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="9469d-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
