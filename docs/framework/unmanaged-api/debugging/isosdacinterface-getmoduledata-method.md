---
title: 'ISOSDacInterface:: GetModuleData, Metoda'
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
ms.openlocfilehash: 14e0eb812c84a0042150345d039451adf178caf1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396922"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="75bae-102">ISOSDacInterface:: GetModuleData, Metoda</span><span class="sxs-lookup"><span data-stu-id="75bae-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="75bae-103">Pobiera dane odpowiadające modułowi załadowanemu pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="75bae-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="75bae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75bae-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="75bae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75bae-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="75bae-106">podczas Adres modułu, dla którego mają zostać pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="75bae-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="75bae-107">określoną [Struktura DacpModuleData](dacpmoduledata-structure.md) do przechowywania informacji o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="75bae-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="75bae-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75bae-108">Remarks</span></span>

<span data-ttu-id="75bae-109">Podana metoda jest częścią `ISOSDacInterface` interfejsu i odpowiada CZTERNASTEMU gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="75bae-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="75bae-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75bae-110">Requirements</span></span>

<span data-ttu-id="75bae-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75bae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="75bae-112">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="75bae-112">**Header:** None</span></span>  
<span data-ttu-id="75bae-113">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="75bae-113">**Library:** None</span></span>  
<span data-ttu-id="75bae-114">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75bae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="75bae-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75bae-115">See also</span></span>

- [<span data-ttu-id="75bae-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="75bae-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="75bae-117">ISOSDacInterface, interfejs</span><span class="sxs-lookup"><span data-stu-id="75bae-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
