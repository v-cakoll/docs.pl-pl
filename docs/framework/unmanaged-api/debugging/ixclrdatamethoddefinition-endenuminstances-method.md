---
title: Metoda IXCLRDataMethodDefinition::EndEnumInstances
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
ms.openlocfilehash: 3d9e3ca31eddff9d08607c4d6d37ca76139bf5d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756306"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="3656b-102">Metoda IXCLRDataMethodDefinition::EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="3656b-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="3656b-103">Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3656b-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3656b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3656b-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="3656b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3656b-105">Parameters</span></span>

`handle`\
<span data-ttu-id="3656b-106">[out] Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3656b-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="3656b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3656b-107">Remarks</span></span>

<span data-ttu-id="3656b-108">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejs i odnosi się do piątego gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="3656b-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="3656b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3656b-109">Requirements</span></span>

<span data-ttu-id="3656b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3656b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3656b-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="3656b-111">**Header:** None</span></span>  
<span data-ttu-id="3656b-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="3656b-112">**Library:** None</span></span>  
<span data-ttu-id="3656b-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3656b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3656b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3656b-114">See also</span></span>

- [<span data-ttu-id="3656b-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3656b-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3656b-116">Interfejs IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="3656b-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
