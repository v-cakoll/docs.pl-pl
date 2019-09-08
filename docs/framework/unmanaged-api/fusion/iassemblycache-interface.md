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
ms.openlocfilehash: 6dab5fe941fce3c23ba718906b29c80c6d257c2f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796768"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="a2eb0-102">IAssemblyCache — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a2eb0-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="a2eb0-103">Reprezentuje globalną pamięć podręczną zestawów do użycia przez technologię Fusion.</span><span class="sxs-lookup"><span data-stu-id="a2eb0-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2eb0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a2eb0-104">Methods</span></span>  
  
|<span data-ttu-id="a2eb0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a2eb0-105">Method</span></span>|<span data-ttu-id="a2eb0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a2eb0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2eb0-107">CreateAssemblyCacheItem, metoda</span><span class="sxs-lookup"><span data-stu-id="a2eb0-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="a2eb0-108">Pobiera odwołanie do nowego [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a2eb0-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="a2eb0-109">CreateAssemblyScavenger, metoda</span><span class="sxs-lookup"><span data-stu-id="a2eb0-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="a2eb0-110">Zarezerwowane do użytku wewnętrznego przez technologię Fusion.</span><span class="sxs-lookup"><span data-stu-id="a2eb0-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="a2eb0-111">InstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="a2eb0-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="a2eb0-112">Instaluje określony zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="a2eb0-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="a2eb0-113">QueryAssemblyInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="a2eb0-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="a2eb0-114">Pobiera żądane dane dotyczące określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a2eb0-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="a2eb0-115">UninstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="a2eb0-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="a2eb0-116">Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="a2eb0-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2eb0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2eb0-117">Requirements</span></span>  
 <span data-ttu-id="a2eb0-118">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2eb0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2eb0-119">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a2eb0-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a2eb0-120">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2eb0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2eb0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2eb0-121">See also</span></span>

- [<span data-ttu-id="a2eb0-122">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="a2eb0-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="a2eb0-123">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="a2eb0-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)
