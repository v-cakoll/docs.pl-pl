---
title: CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 871ad81cd83c40d7299f39ede404e274b95b2ac0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778460"
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="d107a-102">CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d107a-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="d107a-103">Określa atrybuty elementu [iassemblyname — interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu, kiedy jest tworzony przez [createassemblynameobject —](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="d107a-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d107a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d107a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="d107a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d107a-105">Members</span></span>  
  
|<span data-ttu-id="d107a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d107a-106">Member</span></span>|<span data-ttu-id="d107a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d107a-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="d107a-108">Wskazuje, że parametr przekazany jest tekstową tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d107a-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="d107a-109">Ustawia kilka wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="d107a-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="d107a-110">Sprawdza reguły zestawu friend (tylko nazwa i klucz publiczny).</span><span class="sxs-lookup"><span data-stu-id="d107a-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="d107a-111">Ten element jest tylko do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d107a-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="d107a-112">Kombinacji `CANOF_PARSE_DISPLAY_NAME` i `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flag.</span><span class="sxs-lookup"><span data-stu-id="d107a-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="d107a-113">Ten element jest tylko do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d107a-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d107a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d107a-114">Requirements</span></span>  
 <span data-ttu-id="d107a-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d107a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d107a-116">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d107a-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d107a-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d107a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d107a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d107a-118">See also</span></span>

- [<span data-ttu-id="d107a-119">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d107a-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="d107a-120">CreateAssemblyNameObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="d107a-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [<span data-ttu-id="d107a-121">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="d107a-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
