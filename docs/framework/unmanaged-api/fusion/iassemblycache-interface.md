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
ms.openlocfilehash: 5ed0075da1429c70900750f3f28e8ce36a41fb28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134542"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="7e4d4-102">IAssemblyCache — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e4d4-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="7e4d4-103">Reprezentuje globalną pamięć podręczną zestawów do użycia przez technologię Fusion.</span><span class="sxs-lookup"><span data-stu-id="7e4d4-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e4d4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e4d4-104">Methods</span></span>  
  
|<span data-ttu-id="7e4d4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e4d4-105">Method</span></span>|<span data-ttu-id="7e4d4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7e4d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e4d4-107">CreateAssemblyCacheItem, metoda</span><span class="sxs-lookup"><span data-stu-id="7e4d4-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="7e4d4-108">Pobiera odwołanie do nowego [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7e4d4-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="7e4d4-109">CreateAssemblyScavenger, metoda</span><span class="sxs-lookup"><span data-stu-id="7e4d4-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="7e4d4-110">Zarezerwowane do użytku wewnętrznego przez technologię Fusion.</span><span class="sxs-lookup"><span data-stu-id="7e4d4-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="7e4d4-111">InstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="7e4d4-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="7e4d4-112">Instaluje określony zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="7e4d4-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="7e4d4-113">QueryAssemblyInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="7e4d4-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="7e4d4-114">Pobiera żądane dane dotyczące określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7e4d4-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="7e4d4-115">UninstallAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="7e4d4-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="7e4d4-116">Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="7e4d4-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e4d4-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e4d4-117">Requirements</span></span>  
 <span data-ttu-id="7e4d4-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e4d4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e4d4-119">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7e4d4-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7e4d4-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e4d4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e4d4-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e4d4-121">See also</span></span>

- [<span data-ttu-id="7e4d4-122">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="7e4d4-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="7e4d4-123">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="7e4d4-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)
