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
ms.openlocfilehash: c317524cefd7ed654e76bdd7051cdcd7653062db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101793"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="33767-102">CeeSectionAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="33767-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="33767-103">Zawiera wartości, które określają atrybuty sekcji na potrzeby używania przez [iceegen —](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="33767-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33767-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33767-104">Syntax</span></span>  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="33767-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="33767-105">Members</span></span>  
  
|<span data-ttu-id="33767-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="33767-106">Member</span></span>|<span data-ttu-id="33767-107">Opis</span><span class="sxs-lookup"><span data-stu-id="33767-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="33767-108">Sekcja nie ma żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="33767-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="33767-109">Sekcja zawiera zainicjowane dane, które mogą być odczytane tylko, nie zaktualizowano.</span><span class="sxs-lookup"><span data-stu-id="33767-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="33767-110">Sekcja zawiera zainicjowane danych, który może odczytać lub zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="33767-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="33767-111">Sekcja zawiera kod wykonywalny, który może odczytać i wykonywane.</span><span class="sxs-lookup"><span data-stu-id="33767-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33767-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33767-112">Requirements</span></span>  
 <span data-ttu-id="33767-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33767-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33767-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="33767-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33767-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33767-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="33767-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="33767-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33767-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33767-117">See also</span></span>

- [<span data-ttu-id="33767-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="33767-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
