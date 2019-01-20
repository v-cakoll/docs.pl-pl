---
title: Metoda IXCLRDataModule::GetVersionId
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
ms.openlocfilehash: ac4111abdf6a471aca1eca72a86e33698debbff6
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416107"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="1aca8-102">Metoda IXCLRDataModule::GetVersionId</span><span class="sxs-lookup"><span data-stu-id="1aca8-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="1aca8-103">Pobiera identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="1aca8-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1aca8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1aca8-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

### <a name="parameters"></a><span data-ttu-id="1aca8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1aca8-105">Parameters</span></span>

<span data-ttu-id="1aca8-106">`vid` [out] Identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="1aca8-106">`vid` [out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="1aca8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1aca8-107">Remarks</span></span>

<span data-ttu-id="1aca8-108">Podana metoda jest częścią `IXCLRDataModule` interfejs i odnosi się do 40 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="1aca8-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1aca8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1aca8-109">Requirements</span></span>

<span data-ttu-id="1aca8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aca8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1aca8-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="1aca8-111">**Header:** None</span></span>  
<span data-ttu-id="1aca8-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="1aca8-112">**Library:** None</span></span>  
<span data-ttu-id="1aca8-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1aca8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1aca8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aca8-114">See Also</span></span>

- [<span data-ttu-id="1aca8-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1aca8-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="1aca8-116">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="1aca8-116">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
