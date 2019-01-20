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
ms.openlocfilehash: a81da147c1483e7649612050f4aba29a2cc63b49
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416183"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="a71f8-102">Metoda IXCLRDataProcess::StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="a71f8-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="a71f8-103">Zawiera dojście do wyliczenia modułów procesu.</span><span class="sxs-lookup"><span data-stu-id="a71f8-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a71f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a71f8-104">Syntax</span></span>

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="a71f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a71f8-105">Parameters</span></span>

<span data-ttu-id="a71f8-106">`handle` [out] Dojścia wyliczania modułów.</span><span class="sxs-lookup"><span data-stu-id="a71f8-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="a71f8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a71f8-107">Remarks</span></span>

<span data-ttu-id="a71f8-108">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 24 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="a71f8-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a71f8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a71f8-109">Requirements</span></span>

<span data-ttu-id="a71f8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a71f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a71f8-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="a71f8-111">**Header:** None</span></span>  
<span data-ttu-id="a71f8-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="a71f8-112">**Library:** None</span></span>  
<span data-ttu-id="a71f8-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a71f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a71f8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a71f8-114">See Also</span></span>

- [<span data-ttu-id="a71f8-115">Wyliczenie CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="a71f8-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a71f8-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a71f8-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="a71f8-117">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="a71f8-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
