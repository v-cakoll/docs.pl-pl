---
title: Metoda IXCLRDataMethodDefinition::StartEnumInstances
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 208d6c46f18834b23e642efa82df0a365013a410
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416142"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="c2f79-102">Metoda IXCLRDataMethodDefinition::StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="c2f79-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="c2f79-103">Udostępnia dojścia wyliczania wystąpień metody dla danego `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="c2f79-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c2f79-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2f79-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="c2f79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2f79-105">Parameters</span></span>

<span data-ttu-id="c2f79-106">`appDomain` [in] Elementu AppDomain dla wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c2f79-106">`appDomain` [in] An AppDomain for the enumeration.</span></span>

<span data-ttu-id="c2f79-107">`handle` [out] Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="c2f79-107">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2f79-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2f79-108">Remarks</span></span>

<span data-ttu-id="c2f79-109">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejs i odnosi się do trzeciego miejsca, w tabeli wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="c2f79-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2f79-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2f79-110">Requirements</span></span>

<span data-ttu-id="c2f79-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f79-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c2f79-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="c2f79-112">**Header:** None</span></span>  
<span data-ttu-id="c2f79-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="c2f79-113">**Library:** None</span></span>  
<span data-ttu-id="c2f79-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f79-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c2f79-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2f79-115">See Also</span></span>

- [<span data-ttu-id="c2f79-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="c2f79-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="c2f79-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c2f79-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c2f79-118">Interfejs IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="c2f79-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
