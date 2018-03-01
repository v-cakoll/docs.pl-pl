---
title: "ASSEMBLY_INFO — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 215d80c3d207c2f50cfbd74386915b0467692b57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="1c66a-102">ASSEMBLY_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="1c66a-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="1c66a-103">Zawiera informacje dotyczące zestawu, który jest zarejestrowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1c66a-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c66a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c66a-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1c66a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1c66a-105">Members</span></span>  
  
|<span data-ttu-id="1c66a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1c66a-106">Member</span></span>|<span data-ttu-id="1c66a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1c66a-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="1c66a-108">Rozmiar w bajtach struktury.</span><span class="sxs-lookup"><span data-stu-id="1c66a-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="1c66a-109">To pole jest zarezerwowana dla przyszłych rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="1c66a-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="1c66a-110">Flagi, które wskazują szczegóły instalacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="1c66a-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="1c66a-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="1c66a-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="1c66a-112">Wartość ASSEMBLYINFO_FLAG_INSTALLED, co oznacza, że zestaw jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="1c66a-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="1c66a-113">Zawsze Ustawia bieżącą wersję programu .NET Framework `dwAssemblyFlags` tej wartości.</span><span class="sxs-lookup"><span data-stu-id="1c66a-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="1c66a-114">Wartość ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, co oznacza, że zestaw jest rezydentna ładunku.</span><span class="sxs-lookup"><span data-stu-id="1c66a-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="1c66a-115">Bieżąca wersja programu .NET Framework nigdy nie ustawia `dwAssemblyFlags` tej wartości.</span><span class="sxs-lookup"><span data-stu-id="1c66a-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="1c66a-116">Całkowity rozmiar w kilobajtach, plików, które zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="1c66a-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="1c66a-117">Wskaźnik do buforu ciągu, która przechowuje bieżącej ścieżki do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="1c66a-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="1c66a-118">Ścieżka musi kończyć się znakiem null.</span><span class="sxs-lookup"><span data-stu-id="1c66a-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="1c66a-119">Liczba znaki dwubajtowe, włącznie z terminatorem null, która `pszCurrentAssemblyPathBuf` zawiera.</span><span class="sxs-lookup"><span data-stu-id="1c66a-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c66a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c66a-120">Requirements</span></span>  
 <span data-ttu-id="1c66a-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c66a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c66a-122">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1c66a-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1c66a-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c66a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c66a-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c66a-124">See Also</span></span>  
 [<span data-ttu-id="1c66a-125">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="1c66a-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="1c66a-126">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="1c66a-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
