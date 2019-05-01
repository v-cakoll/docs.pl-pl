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
ms.openlocfilehash: e92eea9677731756bdbfcbdcfac1531861fb5dce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961269"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="0ec46-102">Metoda IXCLRDataMethodDefinition::StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="0ec46-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="0ec46-103">Udostępnia dojścia wyliczania wystąpień metody dla danego `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="0ec46-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0ec46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ec46-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="0ec46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ec46-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="0ec46-106">[in] Elementu AppDomain dla wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0ec46-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="0ec46-107">[out] Dojście do wyliczania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0ec46-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ec46-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ec46-108">Remarks</span></span>

<span data-ttu-id="0ec46-109">Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejs i odnosi się do trzeciego miejsca, w tabeli wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="0ec46-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ec46-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ec46-110">Requirements</span></span>

<span data-ttu-id="0ec46-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ec46-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0ec46-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="0ec46-112">**Header:** None</span></span>  
<span data-ttu-id="0ec46-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="0ec46-113">**Library:** None</span></span>  
<span data-ttu-id="0ec46-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0ec46-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0ec46-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ec46-115">See also</span></span>

- [<span data-ttu-id="0ec46-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="0ec46-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0ec46-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0ec46-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0ec46-118">Interfejs IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="0ec46-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)