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
ms.openlocfilehash: a0398d18f9568754231082d63b4c6a2c865d8c6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775274"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="edad0-102">Metoda IXCLRDataProcess::EnumModule</span><span class="sxs-lookup"><span data-stu-id="edad0-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="edad0-103">Wylicza moduły tego procesu.</span><span class="sxs-lookup"><span data-stu-id="edad0-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="edad0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edad0-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="edad0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edad0-105">Parameters</span></span>

`handle`\
<span data-ttu-id="edad0-106">[out w] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="edad0-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="edad0-107">[out] Moduł wyliczany.</span><span class="sxs-lookup"><span data-stu-id="edad0-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="edad0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edad0-108">Remarks</span></span>

<span data-ttu-id="edad0-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 25 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="edad0-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="edad0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edad0-110">Requirements</span></span>

<span data-ttu-id="edad0-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edad0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="edad0-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="edad0-112">**Header:** None</span></span>  
<span data-ttu-id="edad0-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="edad0-113">**Library:** None</span></span>  
<span data-ttu-id="edad0-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="edad0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="edad0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edad0-115">See also</span></span>

- [<span data-ttu-id="edad0-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="edad0-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="edad0-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="edad0-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="edad0-118">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="edad0-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="edad0-119">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="edad0-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
