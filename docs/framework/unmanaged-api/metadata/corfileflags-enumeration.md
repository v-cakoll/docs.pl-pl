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
ms.openlocfilehash: 076d5de3e9d1925e3a030fee4a06a89862105897
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045867"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="335ea-102">CorFileFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="335ea-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="335ea-103">Zawiera wartości, które opisują typ zdefiniowany w wywołaniu pliku [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="335ea-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="335ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="335ea-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="335ea-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="335ea-105">Members</span></span>  
  
|<span data-ttu-id="335ea-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="335ea-106">Member</span></span>|<span data-ttu-id="335ea-107">Opis</span><span class="sxs-lookup"><span data-stu-id="335ea-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="335ea-108">Wskazuje, że plik nie jest plikiem zasobów.</span><span class="sxs-lookup"><span data-stu-id="335ea-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="335ea-109">Wskazuje, czy plik, ewentualnie pliku zasobów, nie zawiera metadanych.</span><span class="sxs-lookup"><span data-stu-id="335ea-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="335ea-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="335ea-110">Requirements</span></span>  
 <span data-ttu-id="335ea-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="335ea-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="335ea-112">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="335ea-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="335ea-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="335ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="335ea-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="335ea-114">See also</span></span>

- [<span data-ttu-id="335ea-115">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="335ea-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
