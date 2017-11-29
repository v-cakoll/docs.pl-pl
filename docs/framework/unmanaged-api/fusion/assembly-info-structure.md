---
title: "ASSEMBLY_INFO — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d532bbd2d338f942c09c4213620468a3361db5f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="46927-102">ASSEMBLY_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="46927-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="46927-103">Zawiera informacje dotyczące zestawu, który jest zarejestrowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="46927-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46927-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46927-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="46927-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="46927-105">Members</span></span>  
  
|<span data-ttu-id="46927-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="46927-106">Member</span></span>|<span data-ttu-id="46927-107">Opis</span><span class="sxs-lookup"><span data-stu-id="46927-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="46927-108">Rozmiar w bajtach struktury.</span><span class="sxs-lookup"><span data-stu-id="46927-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="46927-109">To pole jest zarezerwowana dla przyszłych rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="46927-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="46927-110">Flagi, które wskazują szczegóły instalacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="46927-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="46927-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="46927-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="46927-112">Wartość ASSEMBLYINFO_FLAG_INSTALLED, co oznacza, że zestaw jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="46927-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="46927-113">Zawsze Ustawia bieżącą wersję programu .NET Framework `dwAssemblyFlags` tej wartości.</span><span class="sxs-lookup"><span data-stu-id="46927-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="46927-114">Wartość ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, co oznacza, że zestaw jest rezydentna ładunku.</span><span class="sxs-lookup"><span data-stu-id="46927-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="46927-115">Bieżąca wersja programu .NET Framework nigdy nie ustawia `dwAssemblyFlags` tej wartości.</span><span class="sxs-lookup"><span data-stu-id="46927-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="46927-116">Całkowity rozmiar w kilobajtach, plików, które zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="46927-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="46927-117">Wskaźnik do buforu ciągu, która przechowuje bieżącej ścieżki do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="46927-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="46927-118">Ścieżka musi kończyć się znakiem null.</span><span class="sxs-lookup"><span data-stu-id="46927-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="46927-119">Liczba znaki dwubajtowe, włącznie z terminatorem null, która `pszCurrentAssemblyPathBuf` zawiera.</span><span class="sxs-lookup"><span data-stu-id="46927-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46927-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46927-120">Requirements</span></span>  
 <span data-ttu-id="46927-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46927-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46927-122">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="46927-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="46927-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46927-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46927-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46927-124">See Also</span></span>  
 [<span data-ttu-id="46927-125">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="46927-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="46927-126">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="46927-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
