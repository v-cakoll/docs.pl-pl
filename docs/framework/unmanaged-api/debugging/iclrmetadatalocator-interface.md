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
ms.openlocfilehash: ec92214e33cd1acda8b2702d93deba1f0fb2aaa2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111030"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="681ff-102">ICLRMetadataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="681ff-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="681ff-103">Używany przez warstwę usług dostępu do danych do lokalizowania metadanych zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="681ff-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="681ff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="681ff-104">Methods</span></span>  
  
|<span data-ttu-id="681ff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="681ff-105">Method</span></span>|<span data-ttu-id="681ff-106">Opis</span><span class="sxs-lookup"><span data-stu-id="681ff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="681ff-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="681ff-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="681ff-108">Pobiera metadane obrazu z procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="681ff-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="681ff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="681ff-109">Remarks</span></span>  
 <span data-ttu-id="681ff-110">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="681ff-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="681ff-111">Na przykład implementacja procesu na żywo byłaby inna niż w przypadku zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="681ff-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="681ff-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="681ff-112">Requirements</span></span>  
 <span data-ttu-id="681ff-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="681ff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="681ff-114">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="681ff-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="681ff-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="681ff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="681ff-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="681ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681ff-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="681ff-117">See also</span></span>

- [<span data-ttu-id="681ff-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="681ff-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
