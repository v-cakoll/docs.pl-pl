---
title: CorNativeLinkFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98a83a64a692955d5627e891e7fb3a3ef6f53476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442572"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="d6b09-102">CorNativeLinkFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d6b09-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="d6b09-103">Udostępnia wartości flag używane przez konsolidator podczas łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="d6b09-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6b09-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d6b09-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d6b09-105">Members</span></span>  
  
|<span data-ttu-id="d6b09-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d6b09-106">Member</span></span>|<span data-ttu-id="d6b09-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d6b09-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="d6b09-108">Wskazuje żadnych flag.</span><span class="sxs-lookup"><span data-stu-id="d6b09-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="d6b09-109">Wskazuje `setLastError` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d6b09-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="d6b09-110">Wskazuje `nomangle` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d6b09-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="d6b09-111">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="d6b09-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6b09-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6b09-112">Requirements</span></span>  
 <span data-ttu-id="d6b09-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6b09-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6b09-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6b09-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6b09-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6b09-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6b09-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6b09-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b09-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6b09-117">See Also</span></span>  
 [<span data-ttu-id="d6b09-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d6b09-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
