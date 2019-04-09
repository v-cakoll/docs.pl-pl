---
title: AssemblyRefFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc98b2421d23ffd6dfb716a8cc782b46a9d59ce0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128899"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="e3c6b-102">AssemblyRefFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e3c6b-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="e3c6b-103">Zawiera wartości, które opisano funkcje odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e3c6b-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3c6b-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e3c6b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e3c6b-105">Members</span></span>  
  
|<span data-ttu-id="e3c6b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e3c6b-106">Member</span></span>|<span data-ttu-id="e3c6b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3c6b-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="e3c6b-108">Określa, że odwołanie do zestawu zawiera pełną, bez haszowania informacji o wydawcy zestawu.</span><span class="sxs-lookup"><span data-stu-id="e3c6b-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3c6b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3c6b-109">Requirements</span></span>  
 <span data-ttu-id="e3c6b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c6b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c6b-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e3c6b-111">**Header:** Cor.h</span></span>  
  
 **<span data-ttu-id="e3c6b-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e3c6b-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3c6b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3c6b-113">See also</span></span>

- [<span data-ttu-id="e3c6b-114">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="e3c6b-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="e3c6b-115">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c6b-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="e3c6b-116">DefineAssemblyRef, metoda</span><span class="sxs-lookup"><span data-stu-id="e3c6b-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
