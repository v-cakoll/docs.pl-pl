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
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007510"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="5957b-102">CorThreadSafetyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5957b-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="5957b-103">Określa flagi, aby wybrać opcje bezpieczeństwa wątku.</span><span class="sxs-lookup"><span data-stu-id="5957b-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="5957b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5957b-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="5957b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5957b-105">Members</span></span>

|<span data-ttu-id="5957b-106">Członek</span><span class="sxs-lookup"><span data-stu-id="5957b-106">Member</span></span>|<span data-ttu-id="5957b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5957b-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="5957b-108">Wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="5957b-108">Default value.</span></span> <span data-ttu-id="5957b-109">Analogicznie jak `MDThreadSafetyOff` .</span><span class="sxs-lookup"><span data-stu-id="5957b-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="5957b-110">Wskazuje, że nie można ustawić blokady czytnika/składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="5957b-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="5957b-111">Wskazuje, że można ustawić blokadę czytnika/składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="5957b-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="5957b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5957b-112">Requirements</span></span>

<span data-ttu-id="5957b-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5957b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5957b-114">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5957b-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="5957b-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5957b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5957b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5957b-116">See also</span></span>

- [<span data-ttu-id="5957b-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="5957b-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
