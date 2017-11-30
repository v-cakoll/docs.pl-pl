---
title: "Profiling — Struktury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42762812c9d27073fac34b20df5011b386f05740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-structures"></a><span data-ttu-id="8d2bd-102">Profiling — Struktury</span><span class="sxs-lookup"><span data-stu-id="8d2bd-102">Profiling Structures</span></span>
<span data-ttu-id="8d2bd-103">W tej sekcji opisano niezarządzane struktury, których używa interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="8d2bd-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d2bd-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8d2bd-104">In This Section</span></span>  
 [<span data-ttu-id="8d2bd-105">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="8d2bd-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="8d2bd-106">Udostępnia środowisko uruchomieniowe języka wspólnego z informacjami dotyczącymi zestaw odwołania, który powinien należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8d2bd-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="8d2bd-107">Cor_prf_code_info — struktura</span><span class="sxs-lookup"><span data-stu-id="8d2bd-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="8d2bd-108">Reprezentuje jeden ciągły blok kodu natywnego przechowywane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8d2bd-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="8d2bd-109">Cor_prf_ex_clause_info — struktura</span><span class="sxs-lookup"><span data-stu-id="8d2bd-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="8d2bd-110">Przechowuje informacje dotyczące wystąpienia klauzuli określonego wyjątku i jego skojarzony ramki.</span><span class="sxs-lookup"><span data-stu-id="8d2bd-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="8d2bd-111">Cor_prf_function — struktura</span><span class="sxs-lookup"><span data-stu-id="8d2bd-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="8d2bd-112">Udostępnia reprezentację unikatowy funkcji przez połączenie jej z Identyfikatorem odpowiadającym jej wersji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8d2bd-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="8d2bd-113">Cor_prf_function_argument_info — struktura</span><span class="sxs-lookup"><span data-stu-id="8d2bd-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="8d2bd-114">Reprezentuje argumenty funkcji w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="8d2bd-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="8d2bd-115">Cor_prf_function_argument_range — struktura</span><span class="sxs-lookup"><span data-stu-id="8d2bd-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="8d2bd-116">Reprezentuje blok argumentów funkcji ciągłym przechowywane w kolejności od lewej do prawej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8d2bd-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="8d2bd-117">Cor_prf_gc_generation_range — struktura</span><span class="sxs-lookup"><span data-stu-id="8d2bd-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="8d2bd-118">Opisuje zakres pamięci, która jest poddawana wyrzucanie elementów bezużytecznych (to znaczy bloku).</span><span class="sxs-lookup"><span data-stu-id="8d2bd-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8d2bd-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="8d2bd-119">Related Sections</span></span>  
 <span data-ttu-id="8d2bd-120">COR_DEBUG_IL_TO_NATIVE_MAP —</span><span class="sxs-lookup"><span data-stu-id="8d2bd-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="8d2bd-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="8d2bd-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="8d2bd-122">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="8d2bd-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="8d2bd-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="8d2bd-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="8d2bd-124">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="8d2bd-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="8d2bd-125">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8d2bd-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
