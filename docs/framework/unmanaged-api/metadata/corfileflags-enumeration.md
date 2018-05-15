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
ms.openlocfilehash: 7ecc2f62a6bb8119b7fe06a82aea827a58d04ecb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="9a0ac-102">CorFileFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9a0ac-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="9a0ac-103">Zawiera wartości, które opisują typ zdefiniowany w wywołaniu pliku [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="9a0ac-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a0ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a0ac-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9a0ac-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9a0ac-105">Members</span></span>  
  
|<span data-ttu-id="9a0ac-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9a0ac-106">Member</span></span>|<span data-ttu-id="9a0ac-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9a0ac-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="9a0ac-108">Wskazuje, że plik nie jest plikiem zasobów.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="9a0ac-109">Wskazuje, że plik, być może plik zasobów, nie zawiera metadanych.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a0ac-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a0ac-110">Requirements</span></span>  
 <span data-ttu-id="9a0ac-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a0ac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a0ac-112">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9a0ac-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9a0ac-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a0ac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a0ac-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a0ac-114">See Also</span></span>  
 [<span data-ttu-id="9a0ac-115">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="9a0ac-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
