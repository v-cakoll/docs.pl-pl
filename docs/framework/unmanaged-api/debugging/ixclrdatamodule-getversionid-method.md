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
ms.openlocfilehash: 5bd84f784ea92e7b2ce2465e64972dc84e16a16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744700"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="2f388-102">Metoda IXCLRDataModule::GetVersionId</span><span class="sxs-lookup"><span data-stu-id="2f388-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="2f388-103">Pobiera identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="2f388-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2f388-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f388-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="2f388-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f388-105">Parameters</span></span>

`vid`\
<span data-ttu-id="2f388-106">[out] Identyfikator wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="2f388-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f388-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f388-107">Remarks</span></span>

<span data-ttu-id="2f388-108">Podana metoda jest częścią `IXCLRDataModule` interfejs i odnosi się do 40 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="2f388-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f388-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f388-109">Requirements</span></span>

<span data-ttu-id="2f388-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f388-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2f388-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="2f388-111">**Header:** None</span></span>  
<span data-ttu-id="2f388-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="2f388-112">**Library:** None</span></span>  
<span data-ttu-id="2f388-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2f388-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2f388-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f388-114">See also</span></span>

- [<span data-ttu-id="2f388-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2f388-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="2f388-116">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="2f388-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
