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
ms.openlocfilehash: e5dd77783c03d6a61d0b5831e44db97a731d8074
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825891"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="c7784-102">ICLRMetadataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7784-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="c7784-103">Używane przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="c7784-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7784-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7784-104">Methods</span></span>  
  
|<span data-ttu-id="c7784-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7784-105">Method</span></span>|<span data-ttu-id="c7784-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c7784-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7784-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="c7784-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="c7784-108">Pobiera metadane obrazu z procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c7784-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7784-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7784-109">Remarks</span></span>  
 <span data-ttu-id="c7784-110">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c7784-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="c7784-111">Na przykład to implementacja żywy proces będzie różnić się od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="c7784-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7784-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7784-112">Requirements</span></span>  
 <span data-ttu-id="c7784-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7784-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7784-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c7784-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c7784-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7784-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7784-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7784-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7784-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7784-117">See also</span></span>
- [<span data-ttu-id="c7784-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c7784-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
