---
title: CorCallingConvention — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c27669c8473bd52d3b82a14d570340ac38d1e07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523249"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="d556c-102">CorCallingConvention — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d556c-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="d556c-103">Zawiera wartości, które opisują rodzaje konwencji wywoływania, które zostały wprowadzone w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d556c-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d556c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d556c-104">Syntax</span></span>  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="d556c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d556c-105">Members</span></span>  
  
|<span data-ttu-id="d556c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d556c-106">Member</span></span>|<span data-ttu-id="d556c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d556c-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="d556c-108">Wskazuje domyślną konwencję wywoływania.</span><span class="sxs-lookup"><span data-stu-id="d556c-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="d556c-109">Wskazuje, że ta metoda przyjmuje zmienną liczbę parametrów.</span><span class="sxs-lookup"><span data-stu-id="d556c-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="d556c-110">Wskazuje, że wywołanie się do pola.</span><span class="sxs-lookup"><span data-stu-id="d556c-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="d556c-111">Wskazuje wywołanie do metody lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d556c-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="d556c-112">Wskazuje, że wywołanie jest właściwością.</span><span class="sxs-lookup"><span data-stu-id="d556c-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="d556c-113">Wskazuje, że wywołanie jest niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="d556c-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="d556c-114">Wskazuje wystąpienia metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="d556c-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="d556c-115">Wskazuje wywołania metody, która przyjmuje zmienną liczbę parametrów funkcji PInvoke 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="d556c-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="d556c-116">W tym artykule opisano nieprawidłową wartość 4-bitowy.</span><span class="sxs-lookup"><span data-stu-id="d556c-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="d556c-117">Wskazuje, że Konwencja wywołania jest opisana przez dolnej cztery bity.</span><span class="sxs-lookup"><span data-stu-id="d556c-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="d556c-118">Wskazuje, który opisuje bitu najwyższego `this` parametru.</span><span class="sxs-lookup"><span data-stu-id="d556c-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="d556c-119">Oznacza to, że `this` parametr jest jawnie opisany w podpisie.</span><span class="sxs-lookup"><span data-stu-id="d556c-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="d556c-120">Wskazuje sygnaturę metody ogólnej przy użyciu jawne liczby argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="d556c-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="d556c-121">To poprzedza liczba zwykłych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d556c-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d556c-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d556c-122">Requirements</span></span>  
 <span data-ttu-id="d556c-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d556c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d556c-124">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d556c-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d556c-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d556c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d556c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d556c-126">See also</span></span>
- [<span data-ttu-id="d556c-127">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d556c-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
