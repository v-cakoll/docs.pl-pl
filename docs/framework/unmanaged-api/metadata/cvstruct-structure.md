---
title: Struktura CVStruct
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CVStruct
api_location: mscoree.dll
api_type: COM
f1_keywords: CVStruct
helpviewer_keywords: CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95c1aeb0cacef929e99e5121f29e2f69b320caec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cvstruct-structure"></a><span data-ttu-id="a08d5-102">Struktura CVStruct</span><span class="sxs-lookup"><span data-stu-id="a08d5-102">CVStruct Structure</span></span>
<span data-ttu-id="a08d5-103">Zawiera informacje, które jest używane podczas instalowania obrazu złożonego lub module.</span><span class="sxs-lookup"><span data-stu-id="a08d5-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a08d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a08d5-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="a08d5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a08d5-105">Members</span></span>  
  
|<span data-ttu-id="a08d5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a08d5-106">Member</span></span>|<span data-ttu-id="a08d5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a08d5-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a08d5-108">Główne</span><span class="sxs-lookup"><span data-stu-id="a08d5-108">Major</span></span>|<span data-ttu-id="a08d5-109">Numer kompilacji wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="a08d5-109">Major version build number.</span></span>|  
|<span data-ttu-id="a08d5-110">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="a08d5-110">Minor</span></span>|<span data-ttu-id="a08d5-111">Wersja pomocnicza numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a08d5-111">Minor version build number.</span></span>|  
|<span data-ttu-id="a08d5-112">Sub</span><span class="sxs-lookup"><span data-stu-id="a08d5-112">Sub</span></span>|<span data-ttu-id="a08d5-113">Numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a08d5-113">Sub-build number.</span></span>|  
|<span data-ttu-id="a08d5-114">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="a08d5-114">Build</span></span>|<span data-ttu-id="a08d5-115">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a08d5-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a08d5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a08d5-116">Requirements</span></span>  
 <span data-ttu-id="a08d5-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a08d5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a08d5-118">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a08d5-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a08d5-119">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a08d5-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a08d5-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a08d5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08d5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a08d5-121">See Also</span></span>  
 [<span data-ttu-id="a08d5-122">Metadane struktury</span><span class="sxs-lookup"><span data-stu-id="a08d5-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
