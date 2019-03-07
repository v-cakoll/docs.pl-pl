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
ms.openlocfilehash: d871ca5dfd62dbca309f4ccc3dcedf959033a41e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474166"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="103d6-102">Metoda IXCLRDataProcess::StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="103d6-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="103d6-103">Zawiera dojście do wyliczenia modułów procesu.</span><span class="sxs-lookup"><span data-stu-id="103d6-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="103d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="103d6-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="103d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="103d6-105">Parameters</span></span>

`handle`\
<span data-ttu-id="103d6-106">[out] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="103d6-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="103d6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="103d6-107">Remarks</span></span>

<span data-ttu-id="103d6-108">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 24 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="103d6-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="103d6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="103d6-109">Requirements</span></span>

<span data-ttu-id="103d6-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="103d6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="103d6-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="103d6-111">**Header:** None</span></span>  
<span data-ttu-id="103d6-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="103d6-112">**Library:** None</span></span>  
<span data-ttu-id="103d6-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="103d6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="103d6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="103d6-114">See also</span></span>

- [<span data-ttu-id="103d6-115">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="103d6-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="103d6-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="103d6-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="103d6-117">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="103d6-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
