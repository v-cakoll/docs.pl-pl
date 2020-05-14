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
ms.openlocfilehash: c70920205b27376d453bdd0a13223c6a5569075b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395294"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="96b68-102">IXCLRDataModule:: GetMethodDefinitionByToken, Metoda</span><span class="sxs-lookup"><span data-stu-id="96b68-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="96b68-103">Pobiera definicję metody odpowiadającą danemu tokenowi metadanych.</span><span class="sxs-lookup"><span data-stu-id="96b68-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="96b68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96b68-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="96b68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96b68-105">Parameters</span></span>

`token`\
<span data-ttu-id="96b68-106">podczas Token metody.</span><span class="sxs-lookup"><span data-stu-id="96b68-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="96b68-107">określoną Definicja metody.</span><span class="sxs-lookup"><span data-stu-id="96b68-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="96b68-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96b68-108">Remarks</span></span>

<span data-ttu-id="96b68-109">Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada 26emu miejscu tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="96b68-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="96b68-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96b68-110">Requirements</span></span>

<span data-ttu-id="96b68-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b68-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="96b68-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="96b68-112">**Header:** None</span></span>  
<span data-ttu-id="96b68-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="96b68-113">**Library:** None</span></span>  
<span data-ttu-id="96b68-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="96b68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="96b68-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96b68-115">See also</span></span>

- [<span data-ttu-id="96b68-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="96b68-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="96b68-117">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="96b68-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
