---
title: CorFieldAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: d28a0c8b7ee85f023026dde6f3cc8f3a8406aa64
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450305"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="dca5a-102">CorFieldAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dca5a-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="dca5a-103">Zawiera wartości opisujące metadane dotyczące pola.</span><span class="sxs-lookup"><span data-stu-id="dca5a-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dca5a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="dca5a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dca5a-105">Members</span></span>  
  
|<span data-ttu-id="dca5a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="dca5a-106">Member</span></span>|<span data-ttu-id="dca5a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dca5a-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="dca5a-108">Określa informacje o ułatwieniach dostępu.</span><span class="sxs-lookup"><span data-stu-id="dca5a-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="dca5a-109">Określa, że nie można odwołać się do pola.</span><span class="sxs-lookup"><span data-stu-id="dca5a-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="dca5a-110">Określa, że pole jest dostępne tylko dla jego typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="dca5a-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="dca5a-111">Określa, że pole jest dostępne dla klas pochodnych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="dca5a-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="dca5a-112">Określa, że pole jest dostępne dla wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="dca5a-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="dca5a-113">Określa, że pole jest dostępne tylko na podstawie jego typu i klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="dca5a-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="dca5a-114">Określa, że pole jest dostępne dla klas pochodnych i wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="dca5a-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="dca5a-115">Określa, że pole jest dostępne dla wszystkich typów z widocznością tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="dca5a-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="dca5a-116">Określa, że pole jest elementem członkowskim typu, a nie elementem członkowskim wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dca5a-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="dca5a-117">Określa, że nie można zmienić pola po jego zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="dca5a-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="dca5a-118">Określa, że wartość pola jest stałą czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dca5a-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="dca5a-119">Określa, że pole nie jest serializowane, gdy jego typ jest zdalny.</span><span class="sxs-lookup"><span data-stu-id="dca5a-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="dca5a-120">Określa, że pole jest specjalne i że jego nazwa opisuje sposób.</span><span class="sxs-lookup"><span data-stu-id="dca5a-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="dca5a-121">Określa, że implementacja pola jest przekazywana za pomocą funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="dca5a-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="dca5a-122">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="dca5a-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="dca5a-123">Określa, że wewnętrzne interfejsy API środowiska uruchomieniowego języka wspólnego powinny sprawdzać kodowanie nazwy.</span><span class="sxs-lookup"><span data-stu-id="dca5a-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="dca5a-124">Określa, że pole zawiera informacje o kierowaniu.</span><span class="sxs-lookup"><span data-stu-id="dca5a-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="dca5a-125">Określa, że pole ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="dca5a-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="dca5a-126">Określa, że pole ma względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="dca5a-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dca5a-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dca5a-127">Requirements</span></span>  
 <span data-ttu-id="dca5a-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dca5a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dca5a-129">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="dca5a-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dca5a-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dca5a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca5a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dca5a-131">See also</span></span>

- [<span data-ttu-id="dca5a-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="dca5a-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
