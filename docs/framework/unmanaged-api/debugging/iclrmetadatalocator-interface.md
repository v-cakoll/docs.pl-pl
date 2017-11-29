---
title: "ICLRMetadataLocator — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator
helpviewer_keywords: ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 955bd6bffe56a166b4c9c313fcb730ce714bf24b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="3114d-102">ICLRMetadataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3114d-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="3114d-103">Używane przez warstwę usługi dostępu do danych do lokalizowania metadanych zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="3114d-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3114d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3114d-104">Methods</span></span>  
  
|<span data-ttu-id="3114d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3114d-105">Method</span></span>|<span data-ttu-id="3114d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3114d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3114d-107">GetMetadata — metoda</span><span class="sxs-lookup"><span data-stu-id="3114d-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="3114d-108">Pobiera metadane obrazu z procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3114d-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3114d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3114d-109">Remarks</span></span>  
 <span data-ttu-id="3114d-110">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3114d-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="3114d-111">Na przykład wykonania procesu na żywo będzie innym niż zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="3114d-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3114d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3114d-112">Requirements</span></span>  
 <span data-ttu-id="3114d-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3114d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3114d-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3114d-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3114d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3114d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3114d-116">**.**</span><span class="sxs-lookup"><span data-stu-id="3114d-116">**.**</span></span> <span data-ttu-id="3114d-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3114d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3114d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3114d-118">See Also</span></span>  
 [<span data-ttu-id="3114d-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="3114d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
