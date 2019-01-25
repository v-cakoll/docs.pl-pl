---
title: CorFileFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a614ad1bd9738c993775667ccd261a089e8b57a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624266"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="a9068-102">CorFileFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a9068-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="a9068-103">Zawiera wartości, które opisują typ zdefiniowany w wywołaniu pliku [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a9068-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9068-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9068-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a9068-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a9068-105">Members</span></span>  
  
|<span data-ttu-id="a9068-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a9068-106">Member</span></span>|<span data-ttu-id="a9068-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a9068-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="a9068-108">Wskazuje, że plik nie jest plikiem zasobów.</span><span class="sxs-lookup"><span data-stu-id="a9068-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="a9068-109">Wskazuje, czy plik, ewentualnie pliku zasobów, nie zawiera metadanych.</span><span class="sxs-lookup"><span data-stu-id="a9068-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9068-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9068-110">Requirements</span></span>  
 <span data-ttu-id="a9068-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9068-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9068-112">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a9068-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a9068-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9068-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9068-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9068-114">See also</span></span>
- [<span data-ttu-id="a9068-115">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a9068-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
