---
title: Metoda IXCLRDataProcess::EnumModule
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
ms.openlocfilehash: 40ab90a3218d4309cda709004a191e9440fe505d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769582"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="f15de-102">Metoda IXCLRDataProcess::EnumModule</span><span class="sxs-lookup"><span data-stu-id="f15de-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="f15de-103">Wylicza moduły tego procesu.</span><span class="sxs-lookup"><span data-stu-id="f15de-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f15de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f15de-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="f15de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f15de-105">Parameters</span></span>

`handle`\
<span data-ttu-id="f15de-106">[out w] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="f15de-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="f15de-107">[out] Moduł wyliczany.</span><span class="sxs-lookup"><span data-stu-id="f15de-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="f15de-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f15de-108">Remarks</span></span>

<span data-ttu-id="f15de-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 25 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="f15de-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f15de-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f15de-110">Requirements</span></span>

<span data-ttu-id="f15de-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f15de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f15de-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="f15de-112">**Header:** None</span></span>  
<span data-ttu-id="f15de-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="f15de-113">**Library:** None</span></span>  
<span data-ttu-id="f15de-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f15de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f15de-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f15de-115">See also</span></span>

- [<span data-ttu-id="f15de-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="f15de-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="f15de-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f15de-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="f15de-118">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="f15de-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="f15de-119">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="f15de-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
