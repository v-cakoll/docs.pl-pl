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
ms.openlocfilehash: 1307f555c9d8b6d28febcf25db89ae856c143d71
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009408"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="2d829-102">AssemblyRefFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2d829-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="2d829-103">Zawiera wartości opisujące funkcje odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2d829-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d829-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d829-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2d829-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2d829-105">Members</span></span>  
  
|<span data-ttu-id="2d829-106">Członek</span><span class="sxs-lookup"><span data-stu-id="2d829-106">Member</span></span>|<span data-ttu-id="2d829-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2d829-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="2d829-108">Określa, że odwołanie do zestawu zawiera pełne, niezmieszane informacje o wydawcy zestawu.</span><span class="sxs-lookup"><span data-stu-id="2d829-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d829-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d829-109">Requirements</span></span>  
 <span data-ttu-id="2d829-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d829-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d829-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2d829-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d829-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d829-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d829-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d829-113">See also</span></span>

- [<span data-ttu-id="2d829-114">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="2d829-114">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="2d829-115">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2d829-115">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="2d829-116">DefineAssemblyRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="2d829-116">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
