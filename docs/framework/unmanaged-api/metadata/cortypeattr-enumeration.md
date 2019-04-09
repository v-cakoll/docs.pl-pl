---
title: CorTypeAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e7c973ee22350f26b4f86bcc8b4c4c727291ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087290"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="712b2-102">CorTypeAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="712b2-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="712b2-103">Zawiera wartości, które wskazują metadanych typu.</span><span class="sxs-lookup"><span data-stu-id="712b2-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="712b2-104">Syntax</span></span>  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="712b2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="712b2-105">Members</span></span>  
  
|<span data-ttu-id="712b2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="712b2-106">Member</span></span>|<span data-ttu-id="712b2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="712b2-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="712b2-108">Używane, aby uzyskać informacje o widoczności typu.</span><span class="sxs-lookup"><span data-stu-id="712b2-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="712b2-109">Określa, że typ nie jest w zakresie publicznych.</span><span class="sxs-lookup"><span data-stu-id="712b2-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="712b2-110">Określa, że typ znajduje się w zakresie publicznych.</span><span class="sxs-lookup"><span data-stu-id="712b2-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="712b2-111">Określa, że typ jest zagnieżdżona publicznych wgląd.</span><span class="sxs-lookup"><span data-stu-id="712b2-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="712b2-112">Określa, że typ jest zagnieżdżona prywatnej wgląd.</span><span class="sxs-lookup"><span data-stu-id="712b2-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="712b2-113">Określa, że typ jest zagnieżdżona o widoczności rodziny.</span><span class="sxs-lookup"><span data-stu-id="712b2-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="712b2-114">Określa, że typ jest zagnieżdżona z widocznością zestawu.</span><span class="sxs-lookup"><span data-stu-id="712b2-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="712b2-115">Określa, że typ jest zagnieżdżona o widoczności Rodzina i zestaw.</span><span class="sxs-lookup"><span data-stu-id="712b2-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="712b2-116">Określa, że typ jest zagnieżdżona o widoczności Rodzina lub zestaw.</span><span class="sxs-lookup"><span data-stu-id="712b2-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="712b2-117">Pobiera informacje o układzie dla typu.</span><span class="sxs-lookup"><span data-stu-id="712b2-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="712b2-118">Określa, że pola tego typu są ułożone w automatycznie.</span><span class="sxs-lookup"><span data-stu-id="712b2-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="712b2-119">Określa, że pola tego typu są ułożone w sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="712b2-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="712b2-120">Określa, że układ tego pola jest jawnie podana.</span><span class="sxs-lookup"><span data-stu-id="712b2-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="712b2-121">Pobiera semantycznego informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="712b2-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="712b2-122">Określa, że typ jest klasą.</span><span class="sxs-lookup"><span data-stu-id="712b2-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="712b2-123">Określa, że typ jest interfejsem.</span><span class="sxs-lookup"><span data-stu-id="712b2-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="712b2-124">Określa, że typ jest abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="712b2-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="712b2-125">Określa, że typ nie może zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="712b2-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="712b2-126">Określa, że nazwa klasy jest specjalne.</span><span class="sxs-lookup"><span data-stu-id="712b2-126">Specifies that the class name is special.</span></span> <span data-ttu-id="712b2-127">Nazwy w tym artykule opisano sposób.</span><span class="sxs-lookup"><span data-stu-id="712b2-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="712b2-128">Określa, że typ jest importowany.</span><span class="sxs-lookup"><span data-stu-id="712b2-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="712b2-129">Określa, czy jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="712b2-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="712b2-130">Określa, że ten typ jest [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="712b2-130">Specifies that this type is a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="712b2-131">Pobiera informacje dotyczące sposobu kodowany i sformatowane ciągi.</span><span class="sxs-lookup"><span data-stu-id="712b2-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="712b2-132">Określa, że ten typ interpretuje LPTSTR jako ANSI.</span><span class="sxs-lookup"><span data-stu-id="712b2-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="712b2-133">Określa, że ten typ interpretuje LPTSTR jako Unicode.</span><span class="sxs-lookup"><span data-stu-id="712b2-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="712b2-134">Określa, że ten typ interpretuje LPTSTR automatycznie.</span><span class="sxs-lookup"><span data-stu-id="712b2-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="712b2-135">Określa, że typ ma niestandardowych kodowanie określone przez `CustomFormatMask`.</span><span class="sxs-lookup"><span data-stu-id="712b2-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="712b2-136">Użyj tę maskę, aby pobrać niestandardowych informacji kodowania dla współdziałania z natywnego.</span><span class="sxs-lookup"><span data-stu-id="712b2-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="712b2-137">Znaczenie wartości te dwa bity jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="712b2-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="712b2-138">Określa, że typ musi zostać zainicjowany przed pierwsza próba dostępu do pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="712b2-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="712b2-139">Określa, że typ jest eksportowany, a typ usługi przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="712b2-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="712b2-140">Ta flaga i flagi poniżej są używane wewnętrznie przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="712b2-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="712b2-141">Określa, że środowisko uruchomieniowe języka wspólnego ma sprawdzać, nazwa, kodowanie.</span><span class="sxs-lookup"><span data-stu-id="712b2-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="712b2-142">Określa, że typ ma zabezpieczeń skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="712b2-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="712b2-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="712b2-143">Requirements</span></span>  
 <span data-ttu-id="712b2-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="712b2-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712b2-145">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="712b2-145">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="712b2-146">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="712b2-146">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="712b2-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="712b2-147">See also</span></span>

- [<span data-ttu-id="712b2-148">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="712b2-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
