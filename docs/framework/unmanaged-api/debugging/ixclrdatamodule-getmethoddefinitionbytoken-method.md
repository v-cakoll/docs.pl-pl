---
title: Metoda IXCLRDataModule::GetMethodDefinitionByToken
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 27f1ee28aff95340d4b533473b2f699a9405c3a2
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416188"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="941c0-102">Metoda IXCLRDataModule::GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="941c0-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="941c0-103">Pobiera definicję metody odpowiadającej token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="941c0-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="941c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="941c0-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

### <a name="parameters"></a><span data-ttu-id="941c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="941c0-105">Parameters</span></span>

<span data-ttu-id="941c0-106">`token` [in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="941c0-106">`token` [in] The method token.</span></span>

<span data-ttu-id="941c0-107">`methodDefinition` [out] Definicję metody.</span><span class="sxs-lookup"><span data-stu-id="941c0-107">`methodDefinition` [out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="941c0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="941c0-108">Remarks</span></span>

<span data-ttu-id="941c0-109">Podana metoda jest częścią `IXCLRDataModule` interfejs i odnosi się do 25 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="941c0-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="941c0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="941c0-110">Requirements</span></span>

<span data-ttu-id="941c0-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="941c0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="941c0-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="941c0-112">**Header:** None</span></span>  
<span data-ttu-id="941c0-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="941c0-113">**Library:** None</span></span>  
<span data-ttu-id="941c0-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="941c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="941c0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="941c0-115">See Also</span></span>

- [<span data-ttu-id="941c0-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="941c0-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="941c0-117">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="941c0-117">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
