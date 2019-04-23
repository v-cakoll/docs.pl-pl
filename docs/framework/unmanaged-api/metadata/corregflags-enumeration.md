---
title: CorRegFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb6b303fa7569712c854e8dc4e7513d8608e2519
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104965"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="19f98-102">CorRegFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="19f98-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="19f98-103">Udostępnia wartości flagi używane do rejestracji podczas instalowania modułu lub obrazu złożonego.</span><span class="sxs-lookup"><span data-stu-id="19f98-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f98-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19f98-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="19f98-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="19f98-105">Members</span></span>  
  
|<span data-ttu-id="19f98-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="19f98-106">Member</span></span>|<span data-ttu-id="19f98-107">Opis</span><span class="sxs-lookup"><span data-stu-id="19f98-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="19f98-108">Określa, że nie można skopiować pliki do miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="19f98-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="19f98-109">Określa, czy modułu lub złożone jest konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="19f98-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="19f98-110">Określa, czy moduł lub złożone ma odwołań do klas.</span><span class="sxs-lookup"><span data-stu-id="19f98-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19f98-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19f98-111">Requirements</span></span>  
 <span data-ttu-id="19f98-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19f98-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19f98-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="19f98-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19f98-114">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19f98-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19f98-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19f98-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f98-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19f98-116">See also</span></span>

- [<span data-ttu-id="19f98-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="19f98-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
