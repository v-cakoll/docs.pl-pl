---
title: CeeSectionAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61fc71c2ab0a9107f5e9fbb354fe0f8c2fb0dace
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776336"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="c6552-102">CeeSectionAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c6552-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="c6552-103">Zawiera wartości, które określają atrybuty sekcji na potrzeby używania przez [iceegen —](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c6552-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6552-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6552-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c6552-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c6552-105">Members</span></span>  
  
|<span data-ttu-id="c6552-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c6552-106">Member</span></span>|<span data-ttu-id="c6552-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c6552-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="c6552-108">Sekcja nie ma żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c6552-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="c6552-109">Sekcja zawiera zainicjowane dane, które mogą być odczytane tylko, nie zaktualizowano.</span><span class="sxs-lookup"><span data-stu-id="c6552-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="c6552-110">Sekcja zawiera zainicjowane danych, który może odczytać lub zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="c6552-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="c6552-111">Sekcja zawiera kod wykonywalny, który może odczytać i wykonywane.</span><span class="sxs-lookup"><span data-stu-id="c6552-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6552-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6552-112">Requirements</span></span>  
 <span data-ttu-id="c6552-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6552-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6552-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c6552-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6552-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6552-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6552-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6552-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6552-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6552-117">See also</span></span>

- [<span data-ttu-id="c6552-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="c6552-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
