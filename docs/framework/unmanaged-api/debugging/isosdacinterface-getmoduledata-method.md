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
ms.openlocfilehash: 97b297def9fba329ff6d9573f7b2e7cc811273f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764721"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="fede9-102">Metoda ISOSDacInterface::GetModuleData</span><span class="sxs-lookup"><span data-stu-id="fede9-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="fede9-103">Pobiera dane, odpowiadające moduł, który został załadowany pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="fede9-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fede9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fede9-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="fede9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fede9-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="fede9-106">[in] Adres modułu można pobrać informacji o.</span><span class="sxs-lookup"><span data-stu-id="fede9-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="fede9-107">[out] [Struktury DacpModuleData](dacpmoduledata-structure.md) do przechowywania informacji załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="fede9-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="fede9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fede9-108">Remarks</span></span>

<span data-ttu-id="fede9-109">Podana metoda jest częścią `ISOSDacInterface` interfejs i odnosi się do 13 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="fede9-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fede9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fede9-110">Requirements</span></span>

<span data-ttu-id="fede9-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fede9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fede9-112">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="fede9-112">**Header:** None</span></span>  
<span data-ttu-id="fede9-113">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="fede9-113">**Library:** None</span></span>  
<span data-ttu-id="fede9-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fede9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fede9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fede9-115">See also</span></span>

- [<span data-ttu-id="fede9-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fede9-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="fede9-117">Interfejs ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="fede9-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
