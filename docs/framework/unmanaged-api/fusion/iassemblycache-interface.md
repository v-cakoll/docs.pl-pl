---
title: IAssemblyCache — Interfejs
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fc5f3a3d5bc5699a596bcc648a7153190c130f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697683"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="40e4b-102">IAssemblyCache — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40e4b-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="40e4b-103">Reprezentuje globalnej pamięci podręcznej do użytku przez technologię fusion.</span><span class="sxs-lookup"><span data-stu-id="40e4b-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40e4b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="40e4b-104">Methods</span></span>  
  
|<span data-ttu-id="40e4b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="40e4b-105">Method</span></span>|<span data-ttu-id="40e4b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="40e4b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40e4b-107">CreateAssemblyCacheItem, metoda</span><span class="sxs-lookup"><span data-stu-id="40e4b-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="40e4b-108">Pobiera odwołanie do nowego [iassemblycacheitem —](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="40e4b-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="40e4b-109">CreateAssemblyScavenger, metoda</span><span class="sxs-lookup"><span data-stu-id="40e4b-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="40e4b-110">Zarezerwowane do użytku wewnętrznego przez technologię fusion.</span><span class="sxs-lookup"><span data-stu-id="40e4b-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="40e4b-111">InstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="40e4b-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="40e4b-112">Instaluje określony zestaw w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="40e4b-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="40e4b-113">QueryAssemblyInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="40e4b-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="40e4b-114">Pobiera żądane dane dotyczące określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="40e4b-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="40e4b-115">UninstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="40e4b-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="40e4b-116">Odinstalowuje określony zestaw z globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="40e4b-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40e4b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40e4b-117">Requirements</span></span>  
 <span data-ttu-id="40e4b-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e4b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e4b-119">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="40e4b-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="40e4b-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40e4b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e4b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40e4b-121">See also</span></span>

- [<span data-ttu-id="40e4b-122">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="40e4b-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="40e4b-123">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="40e4b-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
