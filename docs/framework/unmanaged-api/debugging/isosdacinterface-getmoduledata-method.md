---
title: Metoda ISOSDacInterface::GetModuleData
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b0edd459deaf68040e05209c6ecf2cb7cae12e8d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369958"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="512bd-102">Metoda ISOSDacInterface::GetModuleData</span><span class="sxs-lookup"><span data-stu-id="512bd-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="512bd-103">Pobiera dane, odpowiadające moduł, który został załadowany pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="512bd-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="512bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="512bd-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

### <a name="parameters"></a><span data-ttu-id="512bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="512bd-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="512bd-106">[in] Adres modułu można pobrać informacji o.</span><span class="sxs-lookup"><span data-stu-id="512bd-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="512bd-107">[out] [Struktury DacpModuleData](dacpmoduledata-structure.md) do przechowywania informacji załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="512bd-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>


## <a name="remarks"></a><span data-ttu-id="512bd-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="512bd-108">Remarks</span></span>

<span data-ttu-id="512bd-109">Podana metoda jest częścią `ISOSDacInterface` interfejs i odnosi się do 13 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="512bd-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="512bd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="512bd-110">Requirements</span></span>

<span data-ttu-id="512bd-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="512bd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="512bd-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="512bd-112">**Header:** None</span></span>  
<span data-ttu-id="512bd-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="512bd-113">**Library:** None</span></span>  
<span data-ttu-id="512bd-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="512bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="512bd-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="512bd-115">See also</span></span>

- [<span data-ttu-id="512bd-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="512bd-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="512bd-117">Interfejs ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="512bd-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)