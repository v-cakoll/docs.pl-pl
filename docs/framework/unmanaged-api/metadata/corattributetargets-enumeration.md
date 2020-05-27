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
ms.openlocfilehash: f1836f26af99f91ab1765107573f6b067edd5e95
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007926"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="61235-102">CorAttributeTargets — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="61235-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="61235-103">Określa elementy aplikacji, na których jest prawidłowy, aby zastosować atrybut.</span><span class="sxs-lookup"><span data-stu-id="61235-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61235-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61235-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="61235-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="61235-105">Members</span></span>  
  
|<span data-ttu-id="61235-106">Członek</span><span class="sxs-lookup"><span data-stu-id="61235-106">Member</span></span>|<span data-ttu-id="61235-107">Opis</span><span class="sxs-lookup"><span data-stu-id="61235-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="61235-108">Atrybut może zostać zastosowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="61235-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="61235-109">Atrybut można zastosować do przenośnego modułu pliku wykonywalnego (. dll lub. exe).</span><span class="sxs-lookup"><span data-stu-id="61235-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="61235-110">Atrybut może być stosowany do klasy.</span><span class="sxs-lookup"><span data-stu-id="61235-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="61235-111">Atrybut może być stosowany do struktury; oznacza to, że typ wartości.</span><span class="sxs-lookup"><span data-stu-id="61235-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="61235-112">Atrybut może być stosowany do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="61235-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="61235-113">Atrybut może być stosowany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="61235-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="61235-114">Atrybut można zastosować do metody.</span><span class="sxs-lookup"><span data-stu-id="61235-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="61235-115">Atrybut może być stosowany do właściwości.</span><span class="sxs-lookup"><span data-stu-id="61235-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="61235-116">Atrybut może być stosowany do pola.</span><span class="sxs-lookup"><span data-stu-id="61235-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="61235-117">Atrybut może być stosowany do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="61235-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="61235-118">Atrybut może być stosowany do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="61235-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="61235-119">Atrybut może być stosowany do parametru.</span><span class="sxs-lookup"><span data-stu-id="61235-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="61235-120">Atrybut można zastosować do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="61235-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="61235-121">Atrybut może być stosowany do parametru generycznego.</span><span class="sxs-lookup"><span data-stu-id="61235-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="61235-122">Atrybut można zastosować do dowolnego elementu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="61235-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="61235-123">Atrybut można zastosować do składowej klasy.</span><span class="sxs-lookup"><span data-stu-id="61235-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61235-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61235-124">Remarks</span></span>  
 <span data-ttu-id="61235-125">`CorAttributeTargets`Wartości wyliczenia można łączyć z wartością bitową lub operacją w celu uzyskania preferowanej kombinacji.</span><span class="sxs-lookup"><span data-stu-id="61235-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="61235-126">`CorAttributeTargets`Równolegle zarządzanym <xref:System.AttributeTargets?displayProperty=nameWithType> wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="61235-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61235-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61235-127">Requirements</span></span>  
 <span data-ttu-id="61235-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61235-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61235-129">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="61235-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="61235-130">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61235-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61235-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61235-131">See also</span></span>

- [<span data-ttu-id="61235-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="61235-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
