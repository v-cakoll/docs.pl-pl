---
title: CorSerializationType — Wyliczenie
ms.date: 03/30/2017
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
ms.openlocfilehash: 649a9159f99afa64615c40c23a98a80318ae0d7f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009174"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="d3d6b-102">CorSerializationType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d3d6b-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="d3d6b-103">Określa, jak obiekt jest serializowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3d6b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="d3d6b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d3d6b-105">Members</span></span>  
  
|<span data-ttu-id="d3d6b-106">Członek</span><span class="sxs-lookup"><span data-stu-id="d3d6b-106">Member</span></span>|<span data-ttu-id="d3d6b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d3d6b-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="d3d6b-108">Serializacja obiektu jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="d3d6b-109">Obiekt jest serializowany jako typ Boolean</span><span class="sxs-lookup"><span data-stu-id="d3d6b-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="d3d6b-110">Obiekt jest serializowany jako typ znaku.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="d3d6b-111">Obiekt jest serializowany jako 1-bajtowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="d3d6b-112">Serializacja obiektu jest serializowana jako 1-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="d3d6b-113">Obiekt jest serializowany jako 2-bajtowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="d3d6b-114">Serializacja obiektu jest serializowana jako 2-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="d3d6b-115">Serializacja obiektu jest serializowana jako 4-bajtowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="d3d6b-116">Serializacja obiektu jest serializowana jako 4-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="d3d6b-117">Obiekt jest serializowany jako 8-bajtowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="d3d6b-118">Serializacja obiektu jest serializowana jako 8-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="d3d6b-119">Serializacja obiektu jest serializowana jako 4-bajtowy zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="d3d6b-120">Serializacja obiektu jest serializowana jako 8-bajtowy zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="d3d6b-121">Obiekt jest serializowany jako typ System. String.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="d3d6b-122">Serializacja obiektu jest serializowana jako tablica Jednowymiarowa o zerowej granicy.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="d3d6b-123">Serializacja obiektu jest typem ogólnym.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="d3d6b-124">Obiekt jest serializowany jako obiekt otagowany.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="d3d6b-125">Obiekt jest serializowany jako pole.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="d3d6b-126">Obiekt jest serializowany jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="d3d6b-127">Obiekt jest serializowany jako Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="d3d6b-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3d6b-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3d6b-128">Requirements</span></span>  
 <span data-ttu-id="d3d6b-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d6b-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d6b-130">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d3d6b-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d3d6b-131">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d6b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d6b-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3d6b-132">See also</span></span>

- [<span data-ttu-id="d3d6b-133">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d3d6b-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
