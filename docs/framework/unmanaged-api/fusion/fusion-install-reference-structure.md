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
ms.openlocfilehash: 4685d1a23fdf1874817522a16ccd428d81acd1ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433233"
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="2a45a-102">FUSION_INSTALL_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="2a45a-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="2a45a-103">Reprezentuje odwołanie, które umożliwia aplikacji z zestawem aplikacji został zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2a45a-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a45a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a45a-104">Syntax</span></span>  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="2a45a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2a45a-105">Members</span></span>  
  
|<span data-ttu-id="2a45a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2a45a-106">Member</span></span>|<span data-ttu-id="2a45a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2a45a-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="2a45a-108">Rozmiar struktury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2a45a-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="2a45a-109">Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2a45a-109">Reserved for future extensibility.</span></span> <span data-ttu-id="2a45a-110">Ta wartość musi być 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="2a45a-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="2a45a-111">Jednostka, która dodaje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="2a45a-111">The entity that adds the reference.</span></span> <span data-ttu-id="2a45a-112">To pole może mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="2a45a-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="2a45a-113">-FUSION_REFCOUNT_MSI_GUID: Zestaw jest wywoływany przez aplikację, która została zainstalowana przy użyciu Instalatora systemu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="2a45a-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="2a45a-114">`szIdentifier` Pole jest ustawione na `MSI`i `szNonCanonicalData` pole jest ustawione na `Windows Installer`.</span><span class="sxs-lookup"><span data-stu-id="2a45a-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="2a45a-115">Ten schemat jest używany dla zestawów side-by-side systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2a45a-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="2a45a-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Zestaw jest przywoływany przez aplikację, która jest wyświetlana w **Dodaj lub usuń programy** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2a45a-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="2a45a-117">`szIdentifier` Pole zawiera token, który rejestruje aplikację z **Dodaj lub usuń programy** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2a45a-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="2a45a-118">-FUSION_REFCOUNT_FILEPATH_GUID: Zestaw jest wywoływany przez aplikację, która jest reprezentowana przez pliki w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="2a45a-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="2a45a-119">`szIdentifier` Pole zawiera ścieżkę do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="2a45a-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="2a45a-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID: Zestaw jest wywoływany przez aplikację, która odpowiada tylko ciąg z ogólnym opisem.</span><span class="sxs-lookup"><span data-stu-id="2a45a-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="2a45a-121">`szIdentifier` Pole zawiera ten ciąg z ogólnym opisem.</span><span class="sxs-lookup"><span data-stu-id="2a45a-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="2a45a-122">Globalna pamięć podręczna zestawów nie sprawdza istnienie odwołania nieprzezroczyste, po usunięciu tej wartości.</span><span class="sxs-lookup"><span data-stu-id="2a45a-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="2a45a-123">-FUSION_REFCOUNT_OSINSTALL_GUID: Ta wartość jest zastrzeżona.</span><span class="sxs-lookup"><span data-stu-id="2a45a-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="2a45a-124">Unikatowy ciąg, który identyfikuje aplikację, zainstalowanym zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2a45a-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="2a45a-125">Wartość zależy od wartości `guidScheme` pola.</span><span class="sxs-lookup"><span data-stu-id="2a45a-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="2a45a-126">Ciąg, który jest rozpoznawany tylko przez jednostki, która dodaje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="2a45a-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="2a45a-127">Globalna pamięć podręczna zestawów przechowuje ten ciąg, ale nie używa ich.</span><span class="sxs-lookup"><span data-stu-id="2a45a-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a45a-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a45a-128">Requirements</span></span>  
 <span data-ttu-id="2a45a-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a45a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a45a-130">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2a45a-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2a45a-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a45a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a45a-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a45a-132">See Also</span></span>  
 [<span data-ttu-id="2a45a-133">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="2a45a-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="2a45a-134">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="2a45a-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
