---
title: CorValidatorModuleType — Wyliczenie
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97e9ae5a7c35b4f9b6e2b4ca7e754b5b7480dfa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="adbff-102">CorValidatorModuleType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="adbff-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="adbff-103">Określa typ modułu.</span><span class="sxs-lookup"><span data-stu-id="adbff-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adbff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="adbff-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="adbff-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="adbff-105">Members</span></span>  
  
|<span data-ttu-id="adbff-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="adbff-106">Member</span></span>|<span data-ttu-id="adbff-107">Opis</span><span class="sxs-lookup"><span data-stu-id="adbff-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="adbff-108">Moduł jest nieprawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="adbff-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="adbff-109">Minimalna wartość `CorValidatorModuleType` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="adbff-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="adbff-110">Moduł jest plikiem wykonywalnym przenośnego (PE).</span><span class="sxs-lookup"><span data-stu-id="adbff-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="adbff-111">Moduł to plik .obj.</span><span class="sxs-lookup"><span data-stu-id="adbff-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="adbff-112">Moduł jest sesji debugera edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="adbff-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="adbff-113">Moduł to taki, który został utworzony przyrostowo.</span><span class="sxs-lookup"><span data-stu-id="adbff-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="adbff-114">Maksymalna wartość `CorValidatorModuleType` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="adbff-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adbff-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="adbff-115">Requirements</span></span>  
 <span data-ttu-id="adbff-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adbff-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adbff-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="adbff-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="adbff-118">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="adbff-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adbff-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adbff-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adbff-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adbff-120">See Also</span></span>  
 [<span data-ttu-id="adbff-121">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="adbff-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
