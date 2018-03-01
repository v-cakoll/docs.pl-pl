---
title: "CorRegFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f2dcc60d41369250409cccf5b340e98f0cb4ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="fbd3a-102">CorRegFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fbd3a-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="fbd3a-103">Udostępnia wartości flag używane w przypadku rejestracji podczas instalowania modułu lub złożonych obrazu.</span><span class="sxs-lookup"><span data-stu-id="fbd3a-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbd3a-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fbd3a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fbd3a-105">Members</span></span>  
  
|<span data-ttu-id="fbd3a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fbd3a-106">Member</span></span>|<span data-ttu-id="fbd3a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fbd3a-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="fbd3a-108">Określa, że pliki nie powinny być kopiowane do lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="fbd3a-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="fbd3a-109">Określa, czy konfiguracja jest moduł lub złożone.</span><span class="sxs-lookup"><span data-stu-id="fbd3a-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="fbd3a-110">Określa, że moduł lub złożone ma odwołań do klas.</span><span class="sxs-lookup"><span data-stu-id="fbd3a-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbd3a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbd3a-111">Requirements</span></span>  
 <span data-ttu-id="fbd3a-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbd3a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbd3a-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fbd3a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbd3a-114">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbd3a-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fbd3a-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbd3a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd3a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbd3a-116">See Also</span></span>  
 [<span data-ttu-id="fbd3a-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="fbd3a-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
