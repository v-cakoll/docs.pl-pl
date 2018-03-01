---
title: "CorSerializationType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e43151b1611f5b9b8218d30ba46a9143f463c193
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="67826-102">CorSerializationType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="67826-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="67826-103">Określa, jak obiekt jest serializowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="67826-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67826-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67826-104">Syntax</span></span>  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="67826-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="67826-105">Members</span></span>  
  
|<span data-ttu-id="67826-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="67826-106">Member</span></span>|<span data-ttu-id="67826-107">Opis</span><span class="sxs-lookup"><span data-stu-id="67826-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="67826-108">Serializacja obiektu nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="67826-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="67826-109">Serializowany jest obiekt jako typ Boolean</span><span class="sxs-lookup"><span data-stu-id="67826-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="67826-110">Serializowany jest obiekt jako typ znaków.</span><span class="sxs-lookup"><span data-stu-id="67826-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="67826-111">Serializowany jest obiekt jako całkowita 1-bajtowego.</span><span class="sxs-lookup"><span data-stu-id="67826-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="67826-112">Serializowany jest obiekt jako liczba całkowita bez znaku 1-bajtowego.</span><span class="sxs-lookup"><span data-stu-id="67826-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="67826-113">Serializowany jest obiekt jako całkowita 2-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="67826-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="67826-114">Serializowany jest obiekt jako liczba całkowita bez znaku 2-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="67826-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="67826-115">Serializowany jest obiekt jako 4-bajtowych liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="67826-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="67826-116">Serializowany jest obiekt jako liczba całkowita bez znaku 4-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="67826-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="67826-117">Serializowany jest obiekt jako całkowita 8-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="67826-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="67826-118">Serializowany jest obiekt jako liczba całkowita bez znaku 8-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="67826-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="67826-119">Serializowany jest obiekt jako 4-bajtowych zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="67826-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="67826-120">Serializowany jest obiekt jako 8-bajtowych wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="67826-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="67826-121">Serializowany jest obiekt jako typu System.String.</span><span class="sxs-lookup"><span data-stu-id="67826-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="67826-122">Serializowany jest obiekt jako jednowymiarowe, zero dolna granica tablicy.</span><span class="sxs-lookup"><span data-stu-id="67826-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="67826-123">Serializowany jest obiekt jako typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="67826-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="67826-124">Jako obiekt oznakowanych serializowany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="67826-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="67826-125">Serializowany jest obiekt jako pole.</span><span class="sxs-lookup"><span data-stu-id="67826-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="67826-126">Jako właściwość serializowany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="67826-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="67826-127">Jako wyliczenie serializowany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="67826-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67826-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67826-128">Requirements</span></span>  
 <span data-ttu-id="67826-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67826-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67826-130">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="67826-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="67826-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67826-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67826-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67826-132">See Also</span></span>  
 [<span data-ttu-id="67826-133">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="67826-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
