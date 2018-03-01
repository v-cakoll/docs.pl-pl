---
title: "CorValidatorModuleType — Wyliczenie"
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
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3367f6928b5d7378b2686185ee3e03d0279cc11d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="27589-102">CorValidatorModuleType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="27589-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="27589-103">Określa typ modułu.</span><span class="sxs-lookup"><span data-stu-id="27589-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27589-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27589-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="27589-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="27589-105">Members</span></span>  
  
|<span data-ttu-id="27589-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="27589-106">Member</span></span>|<span data-ttu-id="27589-107">Opis</span><span class="sxs-lookup"><span data-stu-id="27589-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="27589-108">Moduł jest nieprawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="27589-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="27589-109">Minimalna wartość `CorValidatorModuleType` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="27589-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="27589-110">Moduł jest plikiem wykonywalnym przenośnego (PE).</span><span class="sxs-lookup"><span data-stu-id="27589-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="27589-111">Moduł to plik .obj.</span><span class="sxs-lookup"><span data-stu-id="27589-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="27589-112">Moduł jest sesji debugera edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="27589-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="27589-113">Moduł to taki, który został utworzony przyrostowo.</span><span class="sxs-lookup"><span data-stu-id="27589-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="27589-114">Maksymalna wartość `CorValidatorModuleType` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="27589-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27589-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27589-115">Requirements</span></span>  
 <span data-ttu-id="27589-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27589-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27589-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27589-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27589-118">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27589-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27589-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27589-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27589-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27589-120">See Also</span></span>  
 [<span data-ttu-id="27589-121">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="27589-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
