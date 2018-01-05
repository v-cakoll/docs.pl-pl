---
title: "CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CREATE_ASM_NAME_OBJ_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords: CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e9bea623e38b1416721773d8739bc6e6748909
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="0fd74-102">CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0fd74-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="0fd74-103">Określa atrybuty [IAssemblyName — interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu, gdy jest tworzony przez [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="0fd74-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fd74-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="0fd74-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0fd74-105">Members</span></span>  
  
|<span data-ttu-id="0fd74-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0fd74-106">Member</span></span>|<span data-ttu-id="0fd74-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd74-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="0fd74-108">Wskazuje, że przekazany parametr jest tożsamości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="0fd74-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="0fd74-109">Ustawia kilka wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="0fd74-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="0fd74-110">Sprawdza, czy reguła zestawu friend (tylko nazwa i klucz publiczny).</span><span class="sxs-lookup"><span data-stu-id="0fd74-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="0fd74-111">Ten element członkowski jest tylko do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0fd74-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="0fd74-112">Kombinację `CANOF_PARSE_DISPLAY_NAME` i `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flagi.</span><span class="sxs-lookup"><span data-stu-id="0fd74-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="0fd74-113">Ten element członkowski jest tylko do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0fd74-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fd74-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fd74-114">Requirements</span></span>  
 <span data-ttu-id="0fd74-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd74-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd74-116">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0fd74-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0fd74-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd74-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd74-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fd74-118">See Also</span></span>  
 [<span data-ttu-id="0fd74-119">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fd74-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="0fd74-120">CreateAssemblyNameObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="0fd74-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [<span data-ttu-id="0fd74-121">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="0fd74-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
