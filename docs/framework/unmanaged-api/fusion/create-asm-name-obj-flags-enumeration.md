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
ms.openlocfilehash: 9897e396424b9076da8f30c61b5a14cfa9539690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795421"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="20545-102">CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="20545-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="20545-103">Określa atrybuty obiektu [interfejsu IAssemblyName](iassemblyname-interface.md) , gdy jest konstruowany [przez funkcję](createassemblynameobject-function.md) myfunctionobject.</span><span class="sxs-lookup"><span data-stu-id="20545-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20545-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20545-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="20545-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="20545-105">Members</span></span>  
  
|<span data-ttu-id="20545-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="20545-106">Member</span></span>|<span data-ttu-id="20545-107">Opis</span><span class="sxs-lookup"><span data-stu-id="20545-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="20545-108">Wskazuje, że przesłany parametr jest tożsamością tekstową.</span><span class="sxs-lookup"><span data-stu-id="20545-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="20545-109">Ustawia kilka wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="20545-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="20545-110">Weryfikuje regułę zaprzyjaźnionego zestawu (tylko nazwę i klucz publiczny).</span><span class="sxs-lookup"><span data-stu-id="20545-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="20545-111">Ten element członkowski jest przeznaczony wyłącznie do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="20545-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="20545-112">Kombinacja `CANOF_PARSE_DISPLAY_NAME` flag i `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` .</span><span class="sxs-lookup"><span data-stu-id="20545-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="20545-113">Ten element członkowski jest przeznaczony wyłącznie do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="20545-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20545-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20545-114">Requirements</span></span>  
 <span data-ttu-id="20545-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20545-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20545-116">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="20545-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="20545-117">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20545-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20545-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20545-118">See also</span></span>

- [<span data-ttu-id="20545-119">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="20545-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="20545-120">CreateAssemblyNameObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="20545-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="20545-121">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="20545-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
