---
title: CorThreadSafetyOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 93dd8c56176890d04d792f3c336492e4f232825b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442471"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="a3c4a-102">CorThreadSafetyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a3c4a-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="a3c4a-103">Określa flagi, aby wybrać opcje bezpieczeństwa wątku.</span><span class="sxs-lookup"><span data-stu-id="a3c4a-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3c4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3c4a-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="a3c4a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a3c4a-105">Members</span></span>

|<span data-ttu-id="a3c4a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a3c4a-106">Member</span></span>|<span data-ttu-id="a3c4a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a3c4a-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="a3c4a-108">Wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="a3c4a-108">Default value.</span></span> <span data-ttu-id="a3c4a-109">Taki sam jak `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="a3c4a-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="a3c4a-110">Wskazuje, że nie można ustawić blokady czytnika/składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="a3c4a-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="a3c4a-111">Wskazuje, że można ustawić blokadę czytnika/składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="a3c4a-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="a3c4a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3c4a-112">Requirements</span></span>

<span data-ttu-id="a3c4a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3c4a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a3c4a-114">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a3c4a-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="a3c4a-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3c4a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a3c4a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3c4a-116">See also</span></span>

- [<span data-ttu-id="a3c4a-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a3c4a-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
