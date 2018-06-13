---
title: ICLRMetadataLocator — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd7a67237d89864915f8b4f1f7361d1f113d1e5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404747"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="f653c-102">ICLRMetadataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f653c-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="f653c-103">Używane przez warstwę usługi dostępu do danych do lokalizowania metadanych zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="f653c-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f653c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f653c-104">Methods</span></span>  
  
|<span data-ttu-id="f653c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f653c-105">Method</span></span>|<span data-ttu-id="f653c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f653c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f653c-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="f653c-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="f653c-108">Pobiera metadane obrazu z procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f653c-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f653c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f653c-109">Remarks</span></span>  
 <span data-ttu-id="f653c-110">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f653c-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="f653c-111">Na przykład wykonania procesu na żywo będzie innym niż zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="f653c-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f653c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f653c-112">Requirements</span></span>  
 <span data-ttu-id="f653c-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f653c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f653c-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f653c-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f653c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f653c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f653c-116">**.**</span><span class="sxs-lookup"><span data-stu-id="f653c-116">**.**</span></span> <span data-ttu-id="f653c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f653c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f653c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f653c-118">See Also</span></span>  
 [<span data-ttu-id="f653c-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f653c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
