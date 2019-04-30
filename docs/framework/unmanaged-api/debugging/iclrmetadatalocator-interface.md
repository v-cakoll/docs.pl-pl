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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697852"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="a9f36-102">ICLRMetadataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a9f36-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="a9f36-103">Używane przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="a9f36-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9f36-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a9f36-104">Methods</span></span>  
  
|<span data-ttu-id="a9f36-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a9f36-105">Method</span></span>|<span data-ttu-id="a9f36-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a9f36-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9f36-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="a9f36-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="a9f36-108">Pobiera metadane obrazu z procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a9f36-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9f36-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9f36-109">Remarks</span></span>  
 <span data-ttu-id="a9f36-110">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a9f36-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="a9f36-111">Na przykład to implementacja żywy proces będzie różnić się od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="a9f36-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9f36-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9f36-112">Requirements</span></span>  
 <span data-ttu-id="a9f36-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9f36-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9f36-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a9f36-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a9f36-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9f36-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9f36-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9f36-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f36-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9f36-117">See also</span></span>

- [<span data-ttu-id="a9f36-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a9f36-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
