---
title: FUSION_INSTALL_REFERENCE — Struktura
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110368"
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="e576d-102">FUSION_INSTALL_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="e576d-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="e576d-103">Reprezentuje odwołanie, który sprawia, że aplikacja do zestawu, który aplikacja została zainstalowana w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e576d-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e576d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e576d-104">Syntax</span></span>  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="e576d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e576d-105">Members</span></span>  
  
|<span data-ttu-id="e576d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e576d-106">Member</span></span>|<span data-ttu-id="e576d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e576d-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="e576d-108">Rozmiar struktury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e576d-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="e576d-109">Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="e576d-109">Reserved for future extensibility.</span></span> <span data-ttu-id="e576d-110">Ta wartość musi być 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="e576d-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="e576d-111">Jednostka, która dodaje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e576d-111">The entity that adds the reference.</span></span> <span data-ttu-id="e576d-112">To pole może mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="e576d-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="e576d-113">-FUSION_REFCOUNT_MSI_GUID: Zestaw odwołuje się aplikacja, która została zainstalowana za pomocą Instalatora Windows firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e576d-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="e576d-114">`szIdentifier` Pole jest ustawione na `MSI`i `szNonCanonicalData` pole jest ustawione na `Windows Installer`.</span><span class="sxs-lookup"><span data-stu-id="e576d-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="e576d-115">Ten schemat jest używany dla zestawów side-by-side Windows.</span><span class="sxs-lookup"><span data-stu-id="e576d-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="e576d-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Zestaw odwołuje się do aplikacji, która jest wyświetlana w **Dodaj/Usuń programy** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e576d-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="e576d-117">`szIdentifier` Pole zawiera token, który rejestruje aplikację za pomocą **Dodaj/Usuń programy** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e576d-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="e576d-118">-FUSION_REFCOUNT_FILEPATH_GUID: Zestaw odwołuje się aplikacja, która jest reprezentowana przez plik w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="e576d-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="e576d-119">`szIdentifier` Pole zawiera ścieżkę do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="e576d-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="e576d-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Zestaw odwołuje się aplikacja, która jest reprezentowana tylko przez nieprzezroczysty ciąg.</span><span class="sxs-lookup"><span data-stu-id="e576d-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="e576d-121">`szIdentifier` Pole zawiera to nieprzezroczysty ciąg.</span><span class="sxs-lookup"><span data-stu-id="e576d-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="e576d-122">Global assembly cache nie sprawdza istnienie odwołania nieprzezroczyste po usunięciu tej wartości.</span><span class="sxs-lookup"><span data-stu-id="e576d-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="e576d-123">-FUSION_REFCOUNT_OSINSTALL_GUID: Ta wartość jest zastrzeżona.</span><span class="sxs-lookup"><span data-stu-id="e576d-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="e576d-124">Unikatowy ciąg, który identyfikuje aplikację, którą zainstalowano zestaw w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e576d-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="e576d-125">Wartość zależy od wartości `guidScheme` pola.</span><span class="sxs-lookup"><span data-stu-id="e576d-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="e576d-126">Ciąg, który jest zrozumiałe dla jednostki, która dodaje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e576d-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="e576d-127">Global assembly cache przechowuje te parametry, ale nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="e576d-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e576d-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e576d-128">Requirements</span></span>  
 <span data-ttu-id="e576d-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e576d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e576d-130">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e576d-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e576d-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e576d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e576d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e576d-132">See also</span></span>

- [<span data-ttu-id="e576d-133">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="e576d-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="e576d-134">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="e576d-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
