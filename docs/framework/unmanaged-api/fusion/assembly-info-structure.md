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
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795488"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="ca4e3-102">ASSEMBLY_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="ca4e3-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="ca4e3-103">Zawiera informacje dotyczące zestawu, który jest zarejestrowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca4e3-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="ca4e3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ca4e3-105">Members</span></span>  
  
|<span data-ttu-id="ca4e3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ca4e3-106">Member</span></span>|<span data-ttu-id="ca4e3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ca4e3-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="ca4e3-108">Rozmiar (w bajtach) struktury.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="ca4e3-109">To pole jest zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="ca4e3-110">Flagi wskazujące szczegóły instalacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="ca4e3-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="ca4e3-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="ca4e3-112">-Wartość ASSEMBLYINFO_FLAG_INSTALLED, która wskazuje, że zestaw jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="ca4e3-113">Bieżąca wersja .NET Framework zawsze jest ustawiana `dwAssemblyFlags` na tę wartość.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="ca4e3-114">-Wartość ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, która wskazuje, że zestaw jest rezydentem ładunku.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="ca4e3-115">Bieżąca wersja .NET Framework nigdy nie ustawia `dwAssemblyFlags` tej wartości.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="ca4e3-116">Łączny rozmiar (w kilobajtach) plików, które zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="ca4e3-117">Wskaźnik do buforu ciągu, który przechowuje bieżącą ścieżkę do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="ca4e3-118">Ścieżka musi kończyć się znakiem null.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="ca4e3-119">Liczba znaków dwubajtowych, łącznie z terminatorem wartości null `pszCurrentAssemblyPathBuf` , który zawiera.</span><span class="sxs-lookup"><span data-stu-id="ca4e3-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca4e3-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca4e3-120">Requirements</span></span>  
 <span data-ttu-id="ca4e3-121">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca4e3-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca4e3-122">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ca4e3-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ca4e3-123">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca4e3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4e3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca4e3-124">See also</span></span>

- [<span data-ttu-id="ca4e3-125">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="ca4e3-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="ca4e3-126">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="ca4e3-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)
