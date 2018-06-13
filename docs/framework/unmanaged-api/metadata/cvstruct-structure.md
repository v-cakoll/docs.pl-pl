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
ms.openlocfilehash: 195f311d58f2169d715bb33986ee6e591622f377
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445046"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="e3864-102">Struktura CVStruct</span><span class="sxs-lookup"><span data-stu-id="e3864-102">CVStruct Structure</span></span>
<span data-ttu-id="e3864-103">Zawiera informacje, które jest używane podczas instalowania obrazu złożonego lub module.</span><span class="sxs-lookup"><span data-stu-id="e3864-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3864-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3864-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="e3864-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e3864-105">Members</span></span>  
  
|<span data-ttu-id="e3864-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e3864-106">Member</span></span>|<span data-ttu-id="e3864-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3864-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e3864-108">Główne</span><span class="sxs-lookup"><span data-stu-id="e3864-108">Major</span></span>|<span data-ttu-id="e3864-109">Numer kompilacji wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="e3864-109">Major version build number.</span></span>|  
|<span data-ttu-id="e3864-110">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="e3864-110">Minor</span></span>|<span data-ttu-id="e3864-111">Wersja pomocnicza numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e3864-111">Minor version build number.</span></span>|  
|<span data-ttu-id="e3864-112">Sub</span><span class="sxs-lookup"><span data-stu-id="e3864-112">Sub</span></span>|<span data-ttu-id="e3864-113">Numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e3864-113">Sub-build number.</span></span>|  
|<span data-ttu-id="e3864-114">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="e3864-114">Build</span></span>|<span data-ttu-id="e3864-115">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e3864-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3864-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3864-116">Requirements</span></span>  
 <span data-ttu-id="e3864-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3864-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3864-118">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e3864-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3864-119">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3864-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3864-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3864-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3864-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3864-121">See Also</span></span>  
 [<span data-ttu-id="e3864-122">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="e3864-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
