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
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796703"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="2bd4d-102">IAssemblyCacheItem — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2bd4d-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="2bd4d-103">Reprezentuje pojedynczy zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2bd4d-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bd4d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2bd4d-104">Methods</span></span>  
  
|<span data-ttu-id="2bd4d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bd4d-105">Method</span></span>|<span data-ttu-id="2bd4d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2bd4d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bd4d-107">AbortItem, metoda</span><span class="sxs-lookup"><span data-stu-id="2bd4d-107">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="2bd4d-108">Zezwala na zestaw w globalnej pamięci podręcznej zestawów na wykonywanie operacji czyszczenia przed jego wydaniem.</span><span class="sxs-lookup"><span data-stu-id="2bd4d-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="2bd4d-109">Commit, metoda</span><span class="sxs-lookup"><span data-stu-id="2bd4d-109">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="2bd4d-110">Zatwierdza odwołanie do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2bd4d-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="2bd4d-111">CreateStream, metoda</span><span class="sxs-lookup"><span data-stu-id="2bd4d-111">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="2bd4d-112">Tworzy strumień o określonej nazwie i formacie.</span><span class="sxs-lookup"><span data-stu-id="2bd4d-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2bd4d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bd4d-113">Requirements</span></span>  
 <span data-ttu-id="2bd4d-114">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bd4d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bd4d-115">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="2bd4d-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2bd4d-116">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bd4d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd4d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bd4d-117">See also</span></span>

- [<span data-ttu-id="2bd4d-118">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="2bd4d-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="2bd4d-119">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="2bd4d-119">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="2bd4d-120">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="2bd4d-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
