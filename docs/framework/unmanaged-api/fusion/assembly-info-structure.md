---
title: ASSEMBLY_INFO — Struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 219a92c0a105cc43e0c2af7d93868cac12f2e4e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778521"
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="3a10c-102">ASSEMBLY_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="3a10c-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="3a10c-103">Zawiera informacje o zestawie, który jest zarejestrowany w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3a10c-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a10c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a10c-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="3a10c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3a10c-105">Members</span></span>  
  
|<span data-ttu-id="3a10c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3a10c-106">Member</span></span>|<span data-ttu-id="3a10c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3a10c-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="3a10c-108">Rozmiar w bajtach, struktury.</span><span class="sxs-lookup"><span data-stu-id="3a10c-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="3a10c-109">To pole jest zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="3a10c-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="3a10c-110">Flagi wskazujące szczegółowe informacje dotyczące instalacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="3a10c-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="3a10c-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="3a10c-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="3a10c-112">-ASSEMBLYINFO_FLAG_INSTALLED wartość, co oznacza, że zestaw jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="3a10c-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="3a10c-113">Zawsze ustawia dla bieżącej wersji programu .NET Framework `dwAssemblyFlags` tej wartości.</span><span class="sxs-lookup"><span data-stu-id="3a10c-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="3a10c-114">-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT wartość, co oznacza, że zestaw jest rezydentnego ładunku.</span><span class="sxs-lookup"><span data-stu-id="3a10c-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="3a10c-115">Bieżąca wersja programu .NET Framework nigdy nie ustawia `dwAssemblyFlags` tej wartości.</span><span class="sxs-lookup"><span data-stu-id="3a10c-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="3a10c-116">Całkowity rozmiar w kilobajtach, plików, które zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="3a10c-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="3a10c-117">Wskaźnik do buforu ciągu, który zawiera bieżącą ścieżkę do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="3a10c-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="3a10c-118">Ścieżka musi kończyć się znakiem null.</span><span class="sxs-lookup"><span data-stu-id="3a10c-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="3a10c-119">Liczba znaków dwubajtowych, łącznie z terminatorem null, która `pszCurrentAssemblyPathBuf` zawiera.</span><span class="sxs-lookup"><span data-stu-id="3a10c-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a10c-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a10c-120">Requirements</span></span>  
 <span data-ttu-id="3a10c-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a10c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a10c-122">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3a10c-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3a10c-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a10c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a10c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a10c-124">See also</span></span>

- [<span data-ttu-id="3a10c-125">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="3a10c-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="3a10c-126">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="3a10c-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
