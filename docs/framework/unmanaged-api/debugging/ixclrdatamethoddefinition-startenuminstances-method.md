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
ms.openlocfilehash: 84e0ad392c5fee8377115427482d80543454fff3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397206"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="1c19a-102">IXCLRDataMethodDefinition:: StartEnumInstances, Metoda</span><span class="sxs-lookup"><span data-stu-id="1c19a-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="1c19a-103">Zapewnia obsługę wyliczania wystąpień metody dla danego elementu `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="1c19a-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1c19a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c19a-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="1c19a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c19a-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="1c19a-106">podczas Element AppDomain dla wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c19a-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="1c19a-107">określoną Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="1c19a-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c19a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c19a-108">Remarks</span></span>

<span data-ttu-id="1c19a-109">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejsu i odpowiada piątemu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="1c19a-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c19a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c19a-110">Requirements</span></span>

<span data-ttu-id="1c19a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c19a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1c19a-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="1c19a-112">**Header:** None</span></span>  
<span data-ttu-id="1c19a-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="1c19a-113">**Library:** None</span></span>  
<span data-ttu-id="1c19a-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c19a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1c19a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c19a-115">See also</span></span>

- [<span data-ttu-id="1c19a-116">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1c19a-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="1c19a-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1c19a-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="1c19a-118">IXCLRDataMethodDefinition, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c19a-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
