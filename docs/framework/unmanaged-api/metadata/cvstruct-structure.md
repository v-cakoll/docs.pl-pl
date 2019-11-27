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
ms.openlocfilehash: 19ee3097dfe80ba9dcbdaf316db0fd165b50abc6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436427"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="8275a-102">Struktura CVStruct</span><span class="sxs-lookup"><span data-stu-id="8275a-102">CVStruct Structure</span></span>
<span data-ttu-id="8275a-103">Zawiera informacje, które są używane podczas instalowania modułu lub obrazu złożonego.</span><span class="sxs-lookup"><span data-stu-id="8275a-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8275a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8275a-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="8275a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8275a-105">Members</span></span>  
  
|<span data-ttu-id="8275a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8275a-106">Member</span></span>|<span data-ttu-id="8275a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8275a-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8275a-108">Duży</span><span class="sxs-lookup"><span data-stu-id="8275a-108">Major</span></span>|<span data-ttu-id="8275a-109">Numer kompilacji wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="8275a-109">Major version build number.</span></span>|  
|<span data-ttu-id="8275a-110">Mały</span><span class="sxs-lookup"><span data-stu-id="8275a-110">Minor</span></span>|<span data-ttu-id="8275a-111">Numer kompilacji wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="8275a-111">Minor version build number.</span></span>|  
|<span data-ttu-id="8275a-112">Sub</span><span class="sxs-lookup"><span data-stu-id="8275a-112">Sub</span></span>|<span data-ttu-id="8275a-113">Numer kompilacji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="8275a-113">Sub-build number.</span></span>|  
|<span data-ttu-id="8275a-114">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="8275a-114">Build</span></span>|<span data-ttu-id="8275a-115">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8275a-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8275a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8275a-116">Requirements</span></span>  
 <span data-ttu-id="8275a-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8275a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8275a-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8275a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8275a-119">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8275a-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8275a-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8275a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8275a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8275a-121">See also</span></span>

- [<span data-ttu-id="8275a-122">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="8275a-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
