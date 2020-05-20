---
title: 'IXCLRDataProcess:: StartEnumModules, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d55b07ea3fada73237919bf677163a9096d5ad04
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420724"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="e5676-102">IXCLRDataProcess:: StartEnumModules, Metoda</span><span class="sxs-lookup"><span data-stu-id="e5676-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="e5676-103">Udostępnia dojście do wyliczenia modułów procesu.</span><span class="sxs-lookup"><span data-stu-id="e5676-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e5676-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5676-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="e5676-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5676-105">Parameters</span></span>

`handle`\
<span data-ttu-id="e5676-106">określoną Dojście do wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="e5676-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5676-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5676-107">Remarks</span></span>

<span data-ttu-id="e5676-108">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 24emu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="e5676-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5676-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5676-109">Requirements</span></span>

<span data-ttu-id="e5676-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5676-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e5676-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="e5676-111">**Header:** None</span></span>  
<span data-ttu-id="e5676-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="e5676-112">**Library:** None</span></span>  
<span data-ttu-id="e5676-113">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5676-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e5676-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5676-114">See also</span></span>

- [<span data-ttu-id="e5676-115">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e5676-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e5676-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e5676-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="e5676-117">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5676-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
