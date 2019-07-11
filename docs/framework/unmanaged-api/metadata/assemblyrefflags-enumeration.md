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
ms.openlocfilehash: c402dcda79f013b19b091c6309b3d71951018a18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776369"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="8a7c2-102">AssemblyRefFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8a7c2-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="8a7c2-103">Zawiera wartości, które opisano funkcje odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a7c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a7c2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8a7c2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8a7c2-105">Members</span></span>  
  
|<span data-ttu-id="8a7c2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8a7c2-106">Member</span></span>|<span data-ttu-id="8a7c2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8a7c2-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="8a7c2-108">Określa, że odwołanie do zestawu zawiera pełną, bez haszowania informacji o wydawcy zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a7c2-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a7c2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a7c2-109">Requirements</span></span>  
 <span data-ttu-id="8a7c2-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a7c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a7c2-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8a7c2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a7c2-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a7c2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7c2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a7c2-113">See also</span></span>

- [<span data-ttu-id="8a7c2-114">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8a7c2-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="8a7c2-115">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a7c2-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="8a7c2-116">DefineAssemblyRef, metoda</span><span class="sxs-lookup"><span data-stu-id="8a7c2-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
