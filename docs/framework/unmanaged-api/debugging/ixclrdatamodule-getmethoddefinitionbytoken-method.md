---
title: 'IXCLRDataModule:: GetMethodDefinitionByToken, Metoda'
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
ms.openlocfilehash: 074949145be588fc34266a9f2ee501caeeffb9d3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420880"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="c3358-102">IXCLRDataModule:: GetMethodDefinitionByToken, Metoda</span><span class="sxs-lookup"><span data-stu-id="c3358-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="c3358-103">Pobiera definicję metody odpowiadającą danemu tokenowi metadanych.</span><span class="sxs-lookup"><span data-stu-id="c3358-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c3358-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3358-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="c3358-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3358-105">Parameters</span></span>

`token`\
<span data-ttu-id="c3358-106">podczas Token metody.</span><span class="sxs-lookup"><span data-stu-id="c3358-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="c3358-107">określoną Definicja metody.</span><span class="sxs-lookup"><span data-stu-id="c3358-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3358-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3358-108">Remarks</span></span>

<span data-ttu-id="c3358-109">Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada 26emu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c3358-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3358-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3358-110">Requirements</span></span>

<span data-ttu-id="c3358-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3358-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c3358-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="c3358-112">**Header:** None</span></span>  
<span data-ttu-id="c3358-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="c3358-113">**Library:** None</span></span>  
<span data-ttu-id="c3358-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c3358-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c3358-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3358-115">See also</span></span>

- [<span data-ttu-id="c3358-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c3358-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="c3358-117">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3358-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
