---
title: IAssemblyCacheItem — Interfejs
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fba17a2ffad9220acdbc79726efe0d3d4184978a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697982"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="57fda-102">IAssemblyCacheItem — Interfejs</span><span class="sxs-lookup"><span data-stu-id="57fda-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="57fda-103">Reprezentuje pojedynczy zestaw w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="57fda-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57fda-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57fda-104">Methods</span></span>  
  
|<span data-ttu-id="57fda-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57fda-105">Method</span></span>|<span data-ttu-id="57fda-106">Opis</span><span class="sxs-lookup"><span data-stu-id="57fda-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57fda-107">AbortItem, metoda</span><span class="sxs-lookup"><span data-stu-id="57fda-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="57fda-108">Umożliwia zestawu w globalnej pamięci podręcznej ma wykonywać operacje czyszczenia, przed jego udostępnieniem.</span><span class="sxs-lookup"><span data-stu-id="57fda-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="57fda-109">Commit, metoda</span><span class="sxs-lookup"><span data-stu-id="57fda-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="57fda-110">Zatwierdza odwołanie do zestawu pamięci podręcznej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="57fda-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="57fda-111">CreateStream, metoda</span><span class="sxs-lookup"><span data-stu-id="57fda-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="57fda-112">Tworzy strumień o określonej nazwie i format.</span><span class="sxs-lookup"><span data-stu-id="57fda-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57fda-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57fda-113">Requirements</span></span>  
 <span data-ttu-id="57fda-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57fda-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57fda-115">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="57fda-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="57fda-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57fda-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57fda-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57fda-117">See also</span></span>

- [<span data-ttu-id="57fda-118">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="57fda-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="57fda-119">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="57fda-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="57fda-120">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="57fda-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
