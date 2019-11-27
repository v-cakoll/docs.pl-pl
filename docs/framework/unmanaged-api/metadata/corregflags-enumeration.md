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
ms.openlocfilehash: 79a9e4513a98a29edc11cc76c599f03c9c3a72b4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450113"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="151ad-102">CorRegFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="151ad-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="151ad-103">Dostarcza wartości flag używanych do rejestracji podczas instalacji modułu lub obrazu złożonego.</span><span class="sxs-lookup"><span data-stu-id="151ad-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="151ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="151ad-104">Syntax</span></span>  
  
```cpp  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="151ad-105">Members</span><span class="sxs-lookup"><span data-stu-id="151ad-105">Members</span></span>  
  
|<span data-ttu-id="151ad-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="151ad-106">Member</span></span>|<span data-ttu-id="151ad-107">Opis</span><span class="sxs-lookup"><span data-stu-id="151ad-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="151ad-108">Określa, że pliki nie powinny być kopiowane do lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="151ad-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="151ad-109">Określa, że moduł lub kompozyt jest konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="151ad-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="151ad-110">Określa, że moduł lub kompozyt zawiera odwołania do klas.</span><span class="sxs-lookup"><span data-stu-id="151ad-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="151ad-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="151ad-111">Requirements</span></span>  
 <span data-ttu-id="151ad-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="151ad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="151ad-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="151ad-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="151ad-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="151ad-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="151ad-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="151ad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151ad-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="151ad-116">See also</span></span>

- [<span data-ttu-id="151ad-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="151ad-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
