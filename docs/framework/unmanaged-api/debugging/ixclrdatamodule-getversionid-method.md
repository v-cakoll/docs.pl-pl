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
ms.openlocfilehash: ff8ccf42d1131fb15d7473ae12ecefde9d55177f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395278"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="b4401-102">IXCLRDataModule:: GetVersionId, Metoda</span><span class="sxs-lookup"><span data-stu-id="b4401-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="b4401-103">Pobiera identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="b4401-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b4401-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4401-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="b4401-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4401-105">Parameters</span></span>

`vid`\
<span data-ttu-id="b4401-106">określoną Identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="b4401-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4401-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4401-107">Remarks</span></span>

<span data-ttu-id="b4401-108">Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada gnieździe 41st tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="b4401-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4401-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4401-109">Requirements</span></span>

<span data-ttu-id="b4401-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4401-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b4401-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="b4401-111">**Header:** None</span></span>  
<span data-ttu-id="b4401-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="b4401-112">**Library:** None</span></span>  
<span data-ttu-id="b4401-113">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4401-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b4401-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4401-114">See also</span></span>

- [<span data-ttu-id="b4401-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b4401-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="b4401-116">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4401-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
