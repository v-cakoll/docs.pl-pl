---
title: 'IXCLRDataModule:: GetVersionId, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9d5ef137a5d76c3d7545ab16921352123e978fb1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420867"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="6e26f-102">IXCLRDataModule:: GetVersionId, Metoda</span><span class="sxs-lookup"><span data-stu-id="6e26f-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="6e26f-103">Pobiera identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="6e26f-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6e26f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e26f-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="6e26f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e26f-105">Parameters</span></span>

`vid`\
<span data-ttu-id="6e26f-106">określoną Identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="6e26f-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e26f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e26f-107">Remarks</span></span>

<span data-ttu-id="6e26f-108">Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada gnieździe 41st tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6e26f-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e26f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e26f-109">Requirements</span></span>

<span data-ttu-id="6e26f-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e26f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6e26f-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="6e26f-111">**Header:** None</span></span>  
<span data-ttu-id="6e26f-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="6e26f-112">**Library:** None</span></span>  
<span data-ttu-id="6e26f-113">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6e26f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6e26f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e26f-114">See also</span></span>

- [<span data-ttu-id="6e26f-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6e26f-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="6e26f-116">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="6e26f-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
