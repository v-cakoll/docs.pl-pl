---
title: "AssemblyRefFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyRefFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyRefFlags
helpviewer_keywords: AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc64d03725df89eac91c85549e287eeb2510037c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="15a01-102">AssemblyRefFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="15a01-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="15a01-103">Zawiera wartości, które opisują funkcje odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="15a01-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15a01-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="15a01-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="15a01-105">Members</span></span>  
  
|<span data-ttu-id="15a01-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="15a01-106">Member</span></span>|<span data-ttu-id="15a01-107">Opis</span><span class="sxs-lookup"><span data-stu-id="15a01-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="15a01-108">Określa, czy odwołanie do zestawu zawiera pełną, bez haszowania informacji o wydawcy zestawu.</span><span class="sxs-lookup"><span data-stu-id="15a01-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15a01-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15a01-109">Requirements</span></span>  
 <span data-ttu-id="15a01-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a01-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a01-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="15a01-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15a01-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a01-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a01-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15a01-113">See Also</span></span>  
 [<span data-ttu-id="15a01-114">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="15a01-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="15a01-115">IMetaDataAssemblyEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="15a01-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="15a01-116">DefineAssemblyRef — metoda</span><span class="sxs-lookup"><span data-stu-id="15a01-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
