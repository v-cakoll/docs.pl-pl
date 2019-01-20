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
ms.openlocfilehash: fa1e41985444324627c6b66a109b4619d85fc57f
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416176"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="cd580-102">Metoda IXCLRDataProcess::EnumModule</span><span class="sxs-lookup"><span data-stu-id="cd580-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="cd580-103">Wylicza moduły tego procesu.</span><span class="sxs-lookup"><span data-stu-id="cd580-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cd580-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd580-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

### <a name="parameters"></a><span data-ttu-id="cd580-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd580-105">Parameters</span></span>

<span data-ttu-id="cd580-106">`handle` [out w] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="cd580-106">`handle` [in, out] A handle for enumerating the modules.</span></span>

<span data-ttu-id="cd580-107">`mod` [out] Moduł wyliczany.</span><span class="sxs-lookup"><span data-stu-id="cd580-107">`mod` [out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd580-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd580-108">Remarks</span></span>

<span data-ttu-id="cd580-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 25 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="cd580-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd580-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd580-110">Requirements</span></span>

<span data-ttu-id="cd580-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd580-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cd580-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="cd580-112">**Header:** None</span></span>  
<span data-ttu-id="cd580-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="cd580-113">**Library:** None</span></span>  
<span data-ttu-id="cd580-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cd580-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cd580-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd580-115">See Also</span></span>

- [<span data-ttu-id="cd580-116">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="cd580-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="cd580-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cd580-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cd580-118">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="cd580-118">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
- [<span data-ttu-id="cd580-119">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="cd580-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
