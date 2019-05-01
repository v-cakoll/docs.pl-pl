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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000444"
---
# <a name="profiling-structures"></a><span data-ttu-id="82069-102">Profiling — Struktury</span><span class="sxs-lookup"><span data-stu-id="82069-102">Profiling Structures</span></span>
<span data-ttu-id="82069-103">W tej sekcji opisano niezarządzane struktury, których używa interfejs profilowania API.</span><span class="sxs-lookup"><span data-stu-id="82069-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82069-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="82069-104">In This Section</span></span>  
 [<span data-ttu-id="82069-105">COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="82069-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="82069-106">Dostarcza informacji na temat zestawu odwołania, należy rozważyć, podczas przeszukiwania zamknięcia odwołanie do zestawu środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="82069-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="82069-107">COR_PRF_CODE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="82069-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="82069-108">Reprezentuje jednym ciągłym bloku kodu natywnego, przechowywane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="82069-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="82069-109">COR_PRF_EX_CLAUSE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="82069-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="82069-110">Przechowuje informacje dotyczące wystąpienia klauzuli określony wyjątek i jego skojarzone ramki.</span><span class="sxs-lookup"><span data-stu-id="82069-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="82069-111">COR_PRF_FUNCTION, struktura</span><span class="sxs-lookup"><span data-stu-id="82069-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="82069-112">Udostępnia reprezentację unikatową funkcję, łącząc się jego Identyfikatorem jego ponownej kompilacji wersji.</span><span class="sxs-lookup"><span data-stu-id="82069-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="82069-113">COR_PRF_FUNCTION_ARGUMENT_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="82069-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="82069-114">Reprezentuje argumenty funkcji, w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="82069-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="82069-115">COR_PRF_FUNCTION_ARGUMENT_RANGE, struktura</span><span class="sxs-lookup"><span data-stu-id="82069-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="82069-116">Reprezentuje blok argumentów funkcji, przechowywane w sposób ciągły w kolejności od lewej do prawej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="82069-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="82069-117">COR_PRF_GC_GENERATION_RANGE, struktura</span><span class="sxs-lookup"><span data-stu-id="82069-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="82069-118">W tym artykule opisano szeroką gamę (czyli bloku) pamięci, która jest w trakcie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82069-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="82069-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="82069-119">Related Sections</span></span>  
 <span data-ttu-id="82069-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="82069-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="82069-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="82069-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="82069-122">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="82069-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="82069-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="82069-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="82069-124">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="82069-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="82069-125">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="82069-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
