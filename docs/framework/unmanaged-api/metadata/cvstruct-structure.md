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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fb73980faa64464c572945fe5ad04e015dc8805b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720655"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="4d7e4-102">Struktura CVStruct</span><span class="sxs-lookup"><span data-stu-id="4d7e4-102">CVStruct Structure</span></span>
<span data-ttu-id="4d7e4-103">Zawiera informacje, które jest używane podczas instalowania modułu lub obrazu złożonego.</span><span class="sxs-lookup"><span data-stu-id="4d7e4-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d7e4-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="4d7e4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4d7e4-105">Members</span></span>  
  
|<span data-ttu-id="4d7e4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4d7e4-106">Member</span></span>|<span data-ttu-id="4d7e4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4d7e4-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4d7e4-108">Duży</span><span class="sxs-lookup"><span data-stu-id="4d7e4-108">Major</span></span>|<span data-ttu-id="4d7e4-109">Numer kompilacji wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="4d7e4-109">Major version build number.</span></span>|  
|<span data-ttu-id="4d7e4-110">Mały</span><span class="sxs-lookup"><span data-stu-id="4d7e4-110">Minor</span></span>|<span data-ttu-id="4d7e4-111">Wersja pomocnicza numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4d7e4-111">Minor version build number.</span></span>|  
|<span data-ttu-id="4d7e4-112">Sub</span><span class="sxs-lookup"><span data-stu-id="4d7e4-112">Sub</span></span>|<span data-ttu-id="4d7e4-113">Numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4d7e4-113">Sub-build number.</span></span>|  
|<span data-ttu-id="4d7e4-114">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="4d7e4-114">Build</span></span>|<span data-ttu-id="4d7e4-115">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4d7e4-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d7e4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d7e4-116">Requirements</span></span>  
 <span data-ttu-id="4d7e4-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d7e4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d7e4-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4d7e4-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d7e4-119">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d7e4-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d7e4-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7e4-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d7e4-121">See also</span></span>
- [<span data-ttu-id="4d7e4-122">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="4d7e4-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
