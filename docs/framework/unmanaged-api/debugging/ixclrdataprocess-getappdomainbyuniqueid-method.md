---
title: IXCLRDataProcess::GetAppDomainByUniqueId Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 83e7d4e1a4ff3c2e6f573d6c097c7cdb9c5f3c54
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416180"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="f9431-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="f9431-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="f9431-103">Pobiera `AppDomain` w oparciu o jego unikatowy identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="f9431-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f9431-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9431-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

### <a name="parameters"></a><span data-ttu-id="f9431-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9431-105">Parameters</span></span>
<span data-ttu-id="f9431-106">`id` [in] Unikatowy identyfikator elementu AppDomain</span><span class="sxs-lookup"><span data-stu-id="f9431-106">`id` [in] The unique identifier of the AppDomain</span></span>

<span data-ttu-id="f9431-107">`appDomain` [out] Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9431-107">`appDomain` [out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="f9431-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9431-108">Remarks</span></span>

<span data-ttu-id="f9431-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 20 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="f9431-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="f9431-110">`IXCLRDataAppDomain*` Zwrócił służy do interakcji z innymi interfejsami API.</span><span class="sxs-lookup"><span data-stu-id="f9431-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9431-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9431-111">Requirements</span></span>
<span data-ttu-id="f9431-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9431-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f9431-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="f9431-113">**Header:** None</span></span>  
<span data-ttu-id="f9431-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="f9431-114">**Library:** None</span></span>  
<span data-ttu-id="f9431-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f9431-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f9431-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9431-116">See Also</span></span>
- [<span data-ttu-id="f9431-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f9431-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f9431-118">Interfejs IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="f9431-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
