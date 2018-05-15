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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d239c3091b29424b26fbab4cb4eb9152ff9ad9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="5a923-102">CorAttributeTargets — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5a923-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="5a923-103">Określa elementy aplikacji, na których jest on prawidłowy do zastosowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5a923-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a923-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a923-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="5a923-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5a923-105">Members</span></span>  
  
|<span data-ttu-id="5a923-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5a923-106">Member</span></span>|<span data-ttu-id="5a923-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5a923-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="5a923-108">Atrybut można stosować do zestawu.</span><span class="sxs-lookup"><span data-stu-id="5a923-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="5a923-109">Atrybut można stosować do przenośnego pliku wykonywalnego modułu (.dll lub .exe).</span><span class="sxs-lookup"><span data-stu-id="5a923-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="5a923-110">Atrybut można stosować do klasy.</span><span class="sxs-lookup"><span data-stu-id="5a923-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="5a923-111">Atrybut można stosować do struktury; oznacza to, że wartość typu.</span><span class="sxs-lookup"><span data-stu-id="5a923-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="5a923-112">Atrybut można stosować do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5a923-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="5a923-113">Atrybut można stosować do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5a923-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="5a923-114">Atrybut można stosować do metody.</span><span class="sxs-lookup"><span data-stu-id="5a923-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="5a923-115">Atrybut można stosować do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a923-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="5a923-116">Atrybut można stosować do pola.</span><span class="sxs-lookup"><span data-stu-id="5a923-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="5a923-117">Atrybut można zastosować do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5a923-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="5a923-118">Atrybut można stosować do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5a923-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="5a923-119">Atrybut można stosować do parametru.</span><span class="sxs-lookup"><span data-stu-id="5a923-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="5a923-120">Atrybut można stosować do delegata.</span><span class="sxs-lookup"><span data-stu-id="5a923-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="5a923-121">Atrybut można stosować do parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="5a923-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="5a923-122">Atrybut można stosować do dowolnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a923-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="5a923-123">Atrybut można stosować do elementu członkowskiego klasy.</span><span class="sxs-lookup"><span data-stu-id="5a923-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a923-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a923-124">Remarks</span></span>  
 <span data-ttu-id="5a923-125">`CorAttributeTargets` Wartości wyliczenia można łączyć z operacji lub pobrać preferowanych kombinacji.</span><span class="sxs-lookup"><span data-stu-id="5a923-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="5a923-126">`CorAttributeTargets` Równoleżnikami zarządzanej <xref:System.AttributeTargets?displayProperty=nameWithType> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5a923-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a923-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a923-127">Requirements</span></span>  
 <span data-ttu-id="5a923-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a923-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a923-129">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5a923-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5a923-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a923-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a923-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a923-131">See Also</span></span>  
 [<span data-ttu-id="5a923-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="5a923-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
