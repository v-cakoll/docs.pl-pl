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
ms.openlocfilehash: d8d7a43848929e49a8cb48fb957f37213ac78f2e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007354"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="d34e7-102">CorRegFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d34e7-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="d34e7-103">Dostarcza wartości flag używanych do rejestracji podczas instalacji modułu lub obrazu złożonego.</span><span class="sxs-lookup"><span data-stu-id="d34e7-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d34e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d34e7-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d34e7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d34e7-105">Members</span></span>  
  
|<span data-ttu-id="d34e7-106">Członek</span><span class="sxs-lookup"><span data-stu-id="d34e7-106">Member</span></span>|<span data-ttu-id="d34e7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d34e7-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="d34e7-108">Określa, że pliki nie powinny być kopiowane do lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="d34e7-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="d34e7-109">Określa, że moduł lub kompozyt jest konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="d34e7-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="d34e7-110">Określa, że moduł lub kompozyt zawiera odwołania do klas.</span><span class="sxs-lookup"><span data-stu-id="d34e7-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d34e7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d34e7-111">Requirements</span></span>  
 <span data-ttu-id="d34e7-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d34e7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d34e7-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d34e7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d34e7-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d34e7-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d34e7-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d34e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d34e7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d34e7-116">See also</span></span>

- [<span data-ttu-id="d34e7-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d34e7-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
