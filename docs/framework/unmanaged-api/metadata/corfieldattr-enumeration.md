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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e909680428c7957da2283d13f5676329d953bf22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781897"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="dd4c1-102">CorFieldAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dd4c1-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="dd4c1-103">Zawiera wartości, które opisują metadane dotyczące pola.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd4c1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dd4c1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dd4c1-105">Members</span></span>  
  
|<span data-ttu-id="dd4c1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="dd4c1-106">Member</span></span>|<span data-ttu-id="dd4c1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dd4c1-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="dd4c1-108">Określa informacje o ułatwieniach dostępu.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="dd4c1-109">Określa, że pole nie może być przywoływany.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="dd4c1-110">Określa, że pole jest dostępne tylko dla typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="dd4c1-111">Określa, że pole jest dostępny przez klasy pochodne w jego zestawie.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="dd4c1-112">Określa, że pole jest dostępne dla wszystkich typów w jego zestawie.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="dd4c1-113">Określa, że pole jest dostępne tylko dla jego typu i klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="dd4c1-114">Określa, że pole jest dostępne, przez klasy pochodne, jak również wszystkie typy w jego zestawie.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="dd4c1-115">Określa, że pole jest dostępne dla wszystkich typów za pomocą widoczność tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="dd4c1-116">Określa, że pole jest elementem członkowskim jego typu, a nie składową wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="dd4c1-117">Określa, że pole nie można zmienić po jego zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="dd4c1-118">Określa, że wartość pola jest stałą czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="dd4c1-119">Określa, czy pole nie jest serializowana, gdy jej typ jest zdalny.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="dd4c1-120">Określa, czy pole ma specjalne i że jego nazwę w tym artykule opisano sposób.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="dd4c1-121">Określa, że implementacja pola jest przekazywany za pomocą usług PInvoke.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="dd4c1-122">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="dd4c1-123">Określa, że typowe metadanych środowiska wykonawczego języka wewnętrznych interfejsach API należy sprawdzać kodowanie nazwy.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="dd4c1-124">Określa, czy pole zawiera informacje dotyczące organizowania.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="dd4c1-125">Określa, że pole ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="dd4c1-126">Określa, że pole ma względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="dd4c1-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd4c1-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd4c1-127">Requirements</span></span>  
 <span data-ttu-id="dd4c1-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd4c1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd4c1-129">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="dd4c1-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dd4c1-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd4c1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4c1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd4c1-131">See also</span></span>

- [<span data-ttu-id="dd4c1-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="dd4c1-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
