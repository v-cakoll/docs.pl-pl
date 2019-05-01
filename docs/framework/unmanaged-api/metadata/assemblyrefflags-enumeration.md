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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043326"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="bd9db-102">AssemblyRefFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bd9db-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="bd9db-103">Zawiera wartości, które opisano funkcje odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="bd9db-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd9db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd9db-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bd9db-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bd9db-105">Members</span></span>  
  
|<span data-ttu-id="bd9db-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bd9db-106">Member</span></span>|<span data-ttu-id="bd9db-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bd9db-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="bd9db-108">Określa, że odwołanie do zestawu zawiera pełną, bez haszowania informacji o wydawcy zestawu.</span><span class="sxs-lookup"><span data-stu-id="bd9db-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd9db-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd9db-109">Requirements</span></span>  
 <span data-ttu-id="bd9db-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd9db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd9db-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bd9db-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd9db-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd9db-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9db-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd9db-113">See also</span></span>

- [<span data-ttu-id="bd9db-114">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="bd9db-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="bd9db-115">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd9db-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="bd9db-116">DefineAssemblyRef, metoda</span><span class="sxs-lookup"><span data-stu-id="bd9db-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
