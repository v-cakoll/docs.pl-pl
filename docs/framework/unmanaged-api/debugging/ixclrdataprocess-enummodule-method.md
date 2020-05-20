---
title: 'IXCLRDataProcess:: EnumModule, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5caadcfe091393a8ff79106d57a50a532c349829
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420781"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="77a6d-102">IXCLRDataProcess:: EnumModule, Metoda</span><span class="sxs-lookup"><span data-stu-id="77a6d-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="77a6d-103">Wylicza moduły tego procesu.</span><span class="sxs-lookup"><span data-stu-id="77a6d-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="77a6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77a6d-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="77a6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77a6d-105">Parameters</span></span>

`handle`\
<span data-ttu-id="77a6d-106">[in. out] Dojście do wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="77a6d-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="77a6d-107">określoną Moduł wyliczany.</span><span class="sxs-lookup"><span data-stu-id="77a6d-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="77a6d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77a6d-108">Remarks</span></span>

<span data-ttu-id="77a6d-109">Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 25 gniazdo tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="77a6d-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="77a6d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77a6d-110">Requirements</span></span>

<span data-ttu-id="77a6d-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77a6d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="77a6d-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="77a6d-112">**Header:** None</span></span>  
<span data-ttu-id="77a6d-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="77a6d-113">**Library:** None</span></span>  
<span data-ttu-id="77a6d-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="77a6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="77a6d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77a6d-115">See also</span></span>

- [<span data-ttu-id="77a6d-116">CLRDataSourceType, Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="77a6d-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="77a6d-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="77a6d-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="77a6d-118">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="77a6d-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="77a6d-119">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="77a6d-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
