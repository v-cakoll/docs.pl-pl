---
title: CorAttributeTargets — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176204"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="bc879-102">CorAttributeTargets — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bc879-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="bc879-103">Określa elementy aplikacji, na których jest prawidłowy, aby zastosować atrybut.</span><span class="sxs-lookup"><span data-stu-id="bc879-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc879-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc879-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="bc879-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bc879-105">Members</span></span>  
  
|<span data-ttu-id="bc879-106">Członek</span><span class="sxs-lookup"><span data-stu-id="bc879-106">Member</span></span>|<span data-ttu-id="bc879-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bc879-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="bc879-108">Atrybut może być stosowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="bc879-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="bc879-109">Atrybut może być stosowany do przenośnego modułu wykonywalnego (.dll lub .exe).</span><span class="sxs-lookup"><span data-stu-id="bc879-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="bc879-110">Atrybut może być stosowany do klasy.</span><span class="sxs-lookup"><span data-stu-id="bc879-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="bc879-111">Atrybut może być stosowany do struktury; oznacza to, że typ wartości.</span><span class="sxs-lookup"><span data-stu-id="bc879-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="bc879-112">Atrybut może być stosowany do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bc879-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="bc879-113">Atrybut może być stosowany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bc879-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="bc879-114">Atrybut może być stosowany do metody.</span><span class="sxs-lookup"><span data-stu-id="bc879-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="bc879-115">Atrybut może być stosowany do właściwości.</span><span class="sxs-lookup"><span data-stu-id="bc879-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="bc879-116">Atrybut można zastosować do pola.</span><span class="sxs-lookup"><span data-stu-id="bc879-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="bc879-117">Atrybut może być stosowany do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bc879-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="bc879-118">Atrybut może być stosowany do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bc879-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="bc879-119">Atrybut może być stosowany do parametru.</span><span class="sxs-lookup"><span data-stu-id="bc879-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="bc879-120">Atrybut można zastosować do pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="bc879-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="bc879-121">Atrybut może być stosowany do parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="bc879-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="bc879-122">Atrybut można zastosować do dowolnego elementu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc879-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="bc879-123">Atrybut może być stosowany do członka klasy.</span><span class="sxs-lookup"><span data-stu-id="bc879-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc879-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc879-124">Remarks</span></span>  
 <span data-ttu-id="bc879-125">Wartości `CorAttributeTargets` wyliczenia można łączyć z bitową operacją OR, aby uzyskać preferowaną kombinację.</span><span class="sxs-lookup"><span data-stu-id="bc879-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="bc879-126">Paralele `CorAttributeTargets` wyliczenia zarządzanego. <xref:System.AttributeTargets?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bc879-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc879-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc879-127">Requirements</span></span>  
 <span data-ttu-id="bc879-128">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc879-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc879-129">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="bc879-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bc879-130">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc879-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc879-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc879-131">See also</span></span>

- [<span data-ttu-id="bc879-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="bc879-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
