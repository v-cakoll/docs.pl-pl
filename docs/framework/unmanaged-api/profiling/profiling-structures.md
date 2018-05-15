---
title: Profiling — Struktury
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 229218cb15963846da91f688b0d2faacb20031c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="profiling-structures"></a><span data-ttu-id="e8fc9-102">Profiling — Struktury</span><span class="sxs-lookup"><span data-stu-id="e8fc9-102">Profiling Structures</span></span>
<span data-ttu-id="e8fc9-103">W tej sekcji opisano niezarządzane struktury, których używa interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="e8fc9-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8fc9-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e8fc9-104">In This Section</span></span>  
 [<span data-ttu-id="e8fc9-105">COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="e8fc9-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="e8fc9-106">Udostępnia środowisko uruchomieniowe języka wspólnego z informacjami dotyczącymi zestaw odwołania, który powinien należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e8fc9-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="e8fc9-107">COR_PRF_CODE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="e8fc9-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="e8fc9-108">Reprezentuje jeden ciągły blok kodu natywnego przechowywane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8fc9-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="e8fc9-109">COR_PRF_EX_CLAUSE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="e8fc9-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="e8fc9-110">Przechowuje informacje dotyczące wystąpienia klauzuli określonego wyjątku i jego skojarzony ramki.</span><span class="sxs-lookup"><span data-stu-id="e8fc9-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="e8fc9-111">COR_PRF_FUNCTION, struktura</span><span class="sxs-lookup"><span data-stu-id="e8fc9-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="e8fc9-112">Udostępnia reprezentację unikatowy funkcji przez połączenie jej z Identyfikatorem odpowiadającym jej wersji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e8fc9-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="e8fc9-113">COR_PRF_FUNCTION_ARGUMENT_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="e8fc9-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="e8fc9-114">Reprezentuje argumenty funkcji w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e8fc9-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="e8fc9-115">COR_PRF_FUNCTION_ARGUMENT_RANGE, struktura</span><span class="sxs-lookup"><span data-stu-id="e8fc9-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="e8fc9-116">Reprezentuje blok argumentów funkcji ciągłym przechowywane w kolejności od lewej do prawej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8fc9-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="e8fc9-117">COR_PRF_GC_GENERATION_RANGE, struktura</span><span class="sxs-lookup"><span data-stu-id="e8fc9-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="e8fc9-118">Opisuje zakres pamięci, która jest poddawana wyrzucanie elementów bezużytecznych (to znaczy bloku).</span><span class="sxs-lookup"><span data-stu-id="e8fc9-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e8fc9-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e8fc9-119">Related Sections</span></span>  
 <span data-ttu-id="e8fc9-120">COR_DEBUG_IL_TO_NATIVE_MAP —</span><span class="sxs-lookup"><span data-stu-id="e8fc9-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="e8fc9-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="e8fc9-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="e8fc9-122">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="e8fc9-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="e8fc9-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="e8fc9-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="e8fc9-124">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="e8fc9-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="e8fc9-125">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e8fc9-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
