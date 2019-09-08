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
ms.openlocfilehash: 9e81fb7c99b9fd03a69456a84f2191770f40121d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795346"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="0b1ca-102">FUSION_INSTALL_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="0b1ca-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="0b1ca-103">Reprezentuje odwołanie do zestawu, który aplikacja została zainstalowana w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b1ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b1ca-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="0b1ca-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0b1ca-105">Members</span></span>  
  
|<span data-ttu-id="0b1ca-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0b1ca-106">Member</span></span>|<span data-ttu-id="0b1ca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0b1ca-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="0b1ca-108">Rozmiar struktury w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="0b1ca-109">Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-109">Reserved for future extensibility.</span></span> <span data-ttu-id="0b1ca-110">Ta wartość musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="0b1ca-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="0b1ca-111">Jednostka, która dodaje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-111">The entity that adds the reference.</span></span> <span data-ttu-id="0b1ca-112">To pole może mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="0b1ca-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="0b1ca-113">- FUSION_REFCOUNT_MSI_GUID: Zestaw jest przywoływany przez aplikację, która została zainstalowana przy użyciu Instalator Windows Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="0b1ca-114">Pole jest ustawione na `MSI`, a `szNonCanonicalData` pole jest ustawione na `Windows Installer`. `szIdentifier`</span><span class="sxs-lookup"><span data-stu-id="0b1ca-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="0b1ca-115">Ten schemat jest używany dla zestawów równoległych systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="0b1ca-116">- FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Zestaw odwołuje się do aplikacji, która pojawia się w interfejsie **Dodaj/Usuń programy** .</span><span class="sxs-lookup"><span data-stu-id="0b1ca-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="0b1ca-117">Pole zawiera token, który rejestruje aplikację przy użyciu interfejsu **Dodaj/Usuń programy.** `szIdentifier`</span><span class="sxs-lookup"><span data-stu-id="0b1ca-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="0b1ca-118">- FUSION_REFCOUNT_FILEPATH_GUID: Zestaw odwołuje się do aplikacji reprezentowanej przez plik w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="0b1ca-119">`szIdentifier` Pole zawiera ścieżkę do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="0b1ca-120">- FUSION_REFCOUNT_OPAQUE_STRING_GUID: Zestaw odwołuje się do aplikacji reprezentowanej tylko przez nieprzezroczysty ciąg.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="0b1ca-121">`szIdentifier` Pole zawiera ten ciąg nieprzezroczysty.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="0b1ca-122">Globalna pamięć podręczna zestawów nie sprawdza istnienia nieprzezroczystych odwołań po usunięciu tej wartości.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="0b1ca-123">- FUSION_REFCOUNT_OSINSTALL_GUID: Ta wartość jest zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="0b1ca-124">Unikatowy ciąg identyfikujący aplikację, która zainstalowała zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="0b1ca-125">Jego wartość zależy od wartości `guidScheme` pola.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="0b1ca-126">Ciąg, który jest zrozumiały tylko dla jednostki, która dodaje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="0b1ca-127">Globalna pamięć podręczna zestawów przechowuje ten ciąg, ale nie używa go.</span><span class="sxs-lookup"><span data-stu-id="0b1ca-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b1ca-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b1ca-128">Requirements</span></span>  
 <span data-ttu-id="0b1ca-129">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b1ca-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b1ca-130">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0b1ca-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0b1ca-131">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b1ca-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1ca-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b1ca-132">See also</span></span>

- [<span data-ttu-id="0b1ca-133">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="0b1ca-133">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="0b1ca-134">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="0b1ca-134">Global Assembly Cache</span></span>](../../app-domains/gac.md)
