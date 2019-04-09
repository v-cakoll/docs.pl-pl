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
ms.openlocfilehash: ddc0429a6fa921e8e6ba3c55f3efe5373bea9576
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123776"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="fa7d3-102">ICLRMetadataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fa7d3-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="fa7d3-103">Używane przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="fa7d3-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa7d3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fa7d3-104">Methods</span></span>  
  
|<span data-ttu-id="fa7d3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fa7d3-105">Method</span></span>|<span data-ttu-id="fa7d3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fa7d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa7d3-107">GetMetadata, metoda</span><span class="sxs-lookup"><span data-stu-id="fa7d3-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="fa7d3-108">Pobiera metadane obrazu z procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fa7d3-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa7d3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa7d3-109">Remarks</span></span>  
 <span data-ttu-id="fa7d3-110">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fa7d3-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="fa7d3-111">Na przykład to implementacja żywy proces będzie różnić się od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="fa7d3-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa7d3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa7d3-112">Requirements</span></span>  
 <span data-ttu-id="fa7d3-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa7d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa7d3-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="fa7d3-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fa7d3-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa7d3-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fa7d3-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fa7d3-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa7d3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa7d3-117">See also</span></span>

- [<span data-ttu-id="fa7d3-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="fa7d3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
