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
ms.openlocfilehash: 8fe6216e11a64ea182d796247d888b862b1e8377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177926"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="4ca23-102">CorRegFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4ca23-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="4ca23-103">Zawiera wartości flag używane do rejestracji podczas instalowania modułu lub obrazu złożonego.</span><span class="sxs-lookup"><span data-stu-id="4ca23-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ca23-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="4ca23-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4ca23-105">Members</span></span>  
  
|<span data-ttu-id="4ca23-106">Członek</span><span class="sxs-lookup"><span data-stu-id="4ca23-106">Member</span></span>|<span data-ttu-id="4ca23-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4ca23-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="4ca23-108">Określa, że pliki nie powinny być kopiowane do miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="4ca23-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="4ca23-109">Określa, że moduł lub kompozyt jest konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="4ca23-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="4ca23-110">Określa, że moduł lub kompozyt ma odwołania do klasy.</span><span class="sxs-lookup"><span data-stu-id="4ca23-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ca23-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ca23-111">Requirements</span></span>  
 <span data-ttu-id="4ca23-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ca23-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ca23-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ca23-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ca23-114">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ca23-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ca23-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ca23-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca23-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ca23-116">See also</span></span>

- [<span data-ttu-id="4ca23-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="4ca23-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
