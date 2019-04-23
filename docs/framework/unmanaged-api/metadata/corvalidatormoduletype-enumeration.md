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
ms.openlocfilehash: 14eee096c25967d321e4693b260501827d944a80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154183"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="20a86-102">CorValidatorModuleType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="20a86-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="20a86-103">Określa typ modułu.</span><span class="sxs-lookup"><span data-stu-id="20a86-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20a86-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="20a86-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="20a86-105">Members</span></span>  
  
|<span data-ttu-id="20a86-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="20a86-106">Member</span></span>|<span data-ttu-id="20a86-107">Opis</span><span class="sxs-lookup"><span data-stu-id="20a86-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="20a86-108">Moduł jest nieprawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="20a86-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="20a86-109">Minimalna wartość `CorValidatorModuleType` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="20a86-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="20a86-110">Moduł jest plikiem przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="20a86-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="20a86-111">Moduł jest plikiem obj.</span><span class="sxs-lookup"><span data-stu-id="20a86-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="20a86-112">Moduł jest sesja debugera edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="20a86-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="20a86-113">Moduł to taki, który został skompilowany przyrostowo.</span><span class="sxs-lookup"><span data-stu-id="20a86-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="20a86-114">Maksymalna wartość `CorValidatorModuleType` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="20a86-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20a86-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20a86-115">Requirements</span></span>  
 <span data-ttu-id="20a86-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20a86-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a86-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="20a86-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20a86-118">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20a86-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20a86-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20a86-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a86-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20a86-120">See also</span></span>

- [<span data-ttu-id="20a86-121">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="20a86-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
