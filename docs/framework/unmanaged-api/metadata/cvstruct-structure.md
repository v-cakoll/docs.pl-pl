---
title: Struktura CVStruct
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: 84791eba7c95d3278bd4650bd7d660e98fcb79d8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008925"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="9d249-102">Struktura CVStruct</span><span class="sxs-lookup"><span data-stu-id="9d249-102">CVStruct Structure</span></span>
<span data-ttu-id="9d249-103">Zawiera informacje, które są używane podczas instalowania modułu lub obrazu złożonego.</span><span class="sxs-lookup"><span data-stu-id="9d249-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d249-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d249-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="9d249-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9d249-105">Members</span></span>  
  
|<span data-ttu-id="9d249-106">Członek</span><span class="sxs-lookup"><span data-stu-id="9d249-106">Member</span></span>|<span data-ttu-id="9d249-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9d249-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9d249-108">Duży</span><span class="sxs-lookup"><span data-stu-id="9d249-108">Major</span></span>|<span data-ttu-id="9d249-109">Numer kompilacji wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="9d249-109">Major version build number.</span></span>|  
|<span data-ttu-id="9d249-110">Mały</span><span class="sxs-lookup"><span data-stu-id="9d249-110">Minor</span></span>|<span data-ttu-id="9d249-111">Numer kompilacji wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="9d249-111">Minor version build number.</span></span>|  
|<span data-ttu-id="9d249-112">Sub</span><span class="sxs-lookup"><span data-stu-id="9d249-112">Sub</span></span>|<span data-ttu-id="9d249-113">Numer kompilacji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9d249-113">Sub-build number.</span></span>|  
|<span data-ttu-id="9d249-114">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="9d249-114">Build</span></span>|<span data-ttu-id="9d249-115">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9d249-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d249-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d249-116">Requirements</span></span>  
 <span data-ttu-id="9d249-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d249-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d249-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9d249-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d249-119">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d249-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d249-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d249-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d249-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d249-121">See also</span></span>

- [<span data-ttu-id="9d249-122">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="9d249-122">Metadata Structures</span></span>](metadata-structures.md)
