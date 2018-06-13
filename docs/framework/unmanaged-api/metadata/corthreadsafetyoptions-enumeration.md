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
ms.openlocfilehash: 3407fcac420b8129dd39eabf84aec84b58651944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442847"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="30f11-102">CorThreadSafetyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="30f11-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="30f11-103">Określa flagi, aby wybrać opcje dla bezpieczeństwa wątków.</span><span class="sxs-lookup"><span data-stu-id="30f11-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30f11-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="30f11-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="30f11-105">Members</span></span>  
  
|<span data-ttu-id="30f11-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="30f11-106">Member</span></span>|<span data-ttu-id="30f11-107">Opis</span><span class="sxs-lookup"><span data-stu-id="30f11-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="30f11-108">Wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="30f11-108">Default value.</span></span> <span data-ttu-id="30f11-109">Taki sam jak `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="30f11-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="30f11-110">Wskazuje, czy czytnik/blokadę nie można ustawić.</span><span class="sxs-lookup"><span data-stu-id="30f11-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="30f11-111">Wskazuje, że można ustawić blokady odczytywania/zapisywania.</span><span class="sxs-lookup"><span data-stu-id="30f11-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30f11-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30f11-112">Requirements</span></span>  
 <span data-ttu-id="30f11-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30f11-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30f11-114">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="30f11-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="30f11-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30f11-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f11-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30f11-116">See Also</span></span>  
 [<span data-ttu-id="30f11-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="30f11-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
