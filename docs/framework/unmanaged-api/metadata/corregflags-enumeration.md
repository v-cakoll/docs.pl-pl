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
ms.openlocfilehash: f7b935b8f59e434c9da364be1986dbed654a1efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445812"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="c467b-102">CorRegFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c467b-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="c467b-103">Udostępnia wartości flag używane w przypadku rejestracji podczas instalowania modułu lub złożonych obrazu.</span><span class="sxs-lookup"><span data-stu-id="c467b-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c467b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c467b-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c467b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c467b-105">Members</span></span>  
  
|<span data-ttu-id="c467b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c467b-106">Member</span></span>|<span data-ttu-id="c467b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c467b-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="c467b-108">Określa, że pliki nie powinny być kopiowane do lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="c467b-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="c467b-109">Określa, czy konfiguracja jest moduł lub złożone.</span><span class="sxs-lookup"><span data-stu-id="c467b-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="c467b-110">Określa, że moduł lub złożone ma odwołań do klas.</span><span class="sxs-lookup"><span data-stu-id="c467b-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c467b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c467b-111">Requirements</span></span>  
 <span data-ttu-id="c467b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c467b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c467b-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c467b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c467b-114">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c467b-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c467b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c467b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c467b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c467b-116">See Also</span></span>  
 [<span data-ttu-id="c467b-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="c467b-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
