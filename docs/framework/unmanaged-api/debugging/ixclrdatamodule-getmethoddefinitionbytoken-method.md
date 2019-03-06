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
ms.openlocfilehash: 727005437289b4bc66ab90f280b80a79f4db06db
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359318"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="6482a-102">Metoda IXCLRDataModule::GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="6482a-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="6482a-103">Pobiera definicję metody odpowiadającej token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="6482a-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6482a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6482a-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="6482a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6482a-105">Parameters</span></span>

`token`\
<span data-ttu-id="6482a-106">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="6482a-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="6482a-107">[out] Definicję metody.</span><span class="sxs-lookup"><span data-stu-id="6482a-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="6482a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6482a-108">Remarks</span></span>

<span data-ttu-id="6482a-109">Podana metoda jest częścią `IXCLRDataModule` interfejs i odnosi się do 25 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="6482a-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6482a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6482a-110">Requirements</span></span>

<span data-ttu-id="6482a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6482a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6482a-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="6482a-112">**Header:** None</span></span>  
<span data-ttu-id="6482a-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="6482a-113">**Library:** None</span></span>  
<span data-ttu-id="6482a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6482a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="6482a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6482a-115">See also</span></span>

- [<span data-ttu-id="6482a-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6482a-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="6482a-117">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="6482a-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
