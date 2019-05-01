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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d71d2a5b3007d4e877900443af426a9643b29125
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045230"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="a37d3-102">CorThreadSafetyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a37d3-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="a37d3-103">Określa flagi, aby wybrać opcje bezpieczeństwo wątkowe.</span><span class="sxs-lookup"><span data-stu-id="a37d3-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="a37d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a37d3-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="a37d3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a37d3-105">Members</span></span>

|<span data-ttu-id="a37d3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a37d3-106">Member</span></span>|<span data-ttu-id="a37d3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a37d3-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="a37d3-108">Wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="a37d3-108">Default value.</span></span> <span data-ttu-id="a37d3-109">Taki sam jak `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="a37d3-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="a37d3-110">Wskazuje, nie można ustawić czytnika/blokadę.</span><span class="sxs-lookup"><span data-stu-id="a37d3-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="a37d3-111">Wskazuje, że czytnik/blokadę można ustawić.</span><span class="sxs-lookup"><span data-stu-id="a37d3-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="a37d3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a37d3-112">Requirements</span></span>

<span data-ttu-id="a37d3-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a37d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a37d3-114">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a37d3-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="a37d3-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a37d3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a37d3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a37d3-116">See also</span></span>

- [<span data-ttu-id="a37d3-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a37d3-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
