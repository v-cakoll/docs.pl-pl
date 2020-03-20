---
title: IXCLRDataModule::Metoda GetMethodDefinitionByToken
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
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176672"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="7867b-102">IXCLRDataModule::Metoda GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="7867b-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="7867b-103">Pobiera definicję metody odpowiadającą tokenowi metadanych.</span><span class="sxs-lookup"><span data-stu-id="7867b-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7867b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7867b-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="7867b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7867b-105">Parameters</span></span>

`token`\
<span data-ttu-id="7867b-106">[w] Token metody.</span><span class="sxs-lookup"><span data-stu-id="7867b-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="7867b-107">[na zewnątrz] Definicja metody.</span><span class="sxs-lookup"><span data-stu-id="7867b-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="7867b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7867b-108">Remarks</span></span>

<span data-ttu-id="7867b-109">Podana metoda jest `IXCLRDataModule` częścią interfejsu i odpowiada 25-sze gniazdo tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="7867b-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7867b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7867b-110">Requirements</span></span>

<span data-ttu-id="7867b-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7867b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7867b-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="7867b-112">**Header:** None</span></span>  
<span data-ttu-id="7867b-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="7867b-113">**Library:** None</span></span>  
<span data-ttu-id="7867b-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7867b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7867b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7867b-115">See also</span></span>

- [<span data-ttu-id="7867b-116">Debugging</span><span class="sxs-lookup"><span data-stu-id="7867b-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="7867b-117">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="7867b-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
