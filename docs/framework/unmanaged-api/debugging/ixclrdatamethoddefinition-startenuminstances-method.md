---
title: 'IXCLRDataMethodDefinition:: StartEnumInstances, Metoda'
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
ms.openlocfilehash: b0c37c666f23f04239ed827246b87c43ee8d5ad9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420932"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="0ea48-102">IXCLRDataMethodDefinition:: StartEnumInstances, Metoda</span><span class="sxs-lookup"><span data-stu-id="0ea48-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="0ea48-103">Zapewnia obsługę wyliczania wystąpień metody dla danego elementu `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="0ea48-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0ea48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ea48-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="0ea48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ea48-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="0ea48-106">podczas Element AppDomain dla wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0ea48-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="0ea48-107">określoną Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0ea48-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ea48-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ea48-108">Remarks</span></span>

<span data-ttu-id="0ea48-109">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejsu i odpowiada piątemu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="0ea48-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ea48-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ea48-110">Requirements</span></span>

<span data-ttu-id="0ea48-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ea48-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0ea48-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="0ea48-112">**Header:** None</span></span>  
<span data-ttu-id="0ea48-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="0ea48-113">**Library:** None</span></span>  
<span data-ttu-id="0ea48-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0ea48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0ea48-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ea48-115">See also</span></span>

- [<span data-ttu-id="0ea48-116">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0ea48-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0ea48-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0ea48-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0ea48-118">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ea48-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
