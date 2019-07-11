---
title: Metoda IXCLRDataProcess::StartEnumModules
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
ms.openlocfilehash: 79c4e0ed99a068d7d806d5c25580dc477aac6475
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752630"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="223b0-102">Metoda IXCLRDataProcess::StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="223b0-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="223b0-103">Zawiera dojście do wyliczenia modułów procesu.</span><span class="sxs-lookup"><span data-stu-id="223b0-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="223b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="223b0-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="223b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="223b0-105">Parameters</span></span>

`handle`\
<span data-ttu-id="223b0-106">[out] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="223b0-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="223b0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="223b0-107">Remarks</span></span>

<span data-ttu-id="223b0-108">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 24 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="223b0-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="223b0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="223b0-109">Requirements</span></span>

<span data-ttu-id="223b0-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="223b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="223b0-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="223b0-111">**Header:** None</span></span>  
<span data-ttu-id="223b0-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="223b0-112">**Library:** None</span></span>  
<span data-ttu-id="223b0-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="223b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="223b0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="223b0-114">See also</span></span>

- [<span data-ttu-id="223b0-115">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="223b0-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="223b0-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="223b0-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="223b0-117">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="223b0-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
