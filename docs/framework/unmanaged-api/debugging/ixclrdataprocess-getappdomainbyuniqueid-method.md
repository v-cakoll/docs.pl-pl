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
ms.openlocfilehash: 257fa2cf03a62ea888b76519aa5c9f9e84038045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126506"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="f5c90-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="f5c90-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="f5c90-103">Pobiera `AppDomain` w oparciu o jego unikatowy identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="f5c90-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f5c90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5c90-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="f5c90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5c90-105">Parameters</span></span>

`id`\
<span data-ttu-id="f5c90-106">[in] Unikatowy identyfikator elementu AppDomain</span><span class="sxs-lookup"><span data-stu-id="f5c90-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="f5c90-107">[out] Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f5c90-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="f5c90-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5c90-108">Remarks</span></span>

<span data-ttu-id="f5c90-109">Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 20 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="f5c90-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="f5c90-110">`IXCLRDataAppDomain*` Zwrócił służy do interakcji z innymi interfejsami API.</span><span class="sxs-lookup"><span data-stu-id="f5c90-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5c90-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5c90-111">Requirements</span></span>
<span data-ttu-id="f5c90-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c90-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f5c90-113">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="f5c90-113">**Header:** None</span></span>  
<span data-ttu-id="f5c90-114">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="f5c90-114">**Library:** None</span></span>  
**<span data-ttu-id="f5c90-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f5c90-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="f5c90-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5c90-116">See also</span></span>

- [<span data-ttu-id="f5c90-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f5c90-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="f5c90-118">IXCLRDataProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c90-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
