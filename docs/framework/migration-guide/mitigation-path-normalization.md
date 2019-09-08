---
title: Środki zaradcze Normalizacja ścieżki
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5ea69d80a225adfc2f409e8303ee1c241398db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779343"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="d0d36-102">Środki zaradcze Normalizacja ścieżki</span><span class="sxs-lookup"><span data-stu-id="d0d36-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="d0d36-103">Począwszy od aplikacji obiekt docelowy .NET Framework 4.6.2, normalizacja ścieżki w .NET Framework została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="d0d36-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="d0d36-104">Co to jest normalizacja ścieżki?</span><span class="sxs-lookup"><span data-stu-id="d0d36-104">What is path normalization?</span></span>  
 <span data-ttu-id="d0d36-105">Normalizowanie ścieżki polega na zmodyfikowaniu ciągu, który identyfikuje ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="d0d36-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="d0d36-106">Normalizacja zazwyczaj obejmuje:</span><span class="sxs-lookup"><span data-stu-id="d0d36-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="d0d36-107">Separatory składników formę kanoniczną działa i katalogów.</span><span class="sxs-lookup"><span data-stu-id="d0d36-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="d0d36-108">Zastosowanie bieżącego katalogu do ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="d0d36-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="d0d36-109">Ocenianie katalogu względnego (`.`) lub katalogu nadrzędnego (`..`) w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="d0d36-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="d0d36-110">Przycinanie określonych znaków.</span><span class="sxs-lookup"><span data-stu-id="d0d36-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="d0d36-111">Zmiany</span><span class="sxs-lookup"><span data-stu-id="d0d36-111">The changes</span></span>  
 <span data-ttu-id="d0d36-112">Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, normalizacja ścieżki zmieniła się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d0d36-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="d0d36-113">Środowisko uruchomieniowe odkłada do funkcji [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) systemu operacyjnego, aby znormalizować ścieżki.</span><span class="sxs-lookup"><span data-stu-id="d0d36-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="d0d36-114">Normalizacja nie obejmuje już przecinania końców segmentów katalogów (takich jak spacja na końcu nazwy katalogu).</span><span class="sxs-lookup"><span data-stu-id="d0d36-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="d0d36-115">Obsługa składni ścieżki urządzenia w pełnym zaufaniu, w `\\.\` tym i dla interfejsów API we/wy plików w bibliotece Mscorlib. `\\?\`dll,.</span><span class="sxs-lookup"><span data-stu-id="d0d36-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="d0d36-116">Środowisko uruchomieniowe nie sprawdza poprawności ścieżek składni urządzeń.</span><span class="sxs-lookup"><span data-stu-id="d0d36-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="d0d36-117">Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.</span><span class="sxs-lookup"><span data-stu-id="d0d36-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d0d36-118">Wpływ</span><span class="sxs-lookup"><span data-stu-id="d0d36-118">Impact</span></span>  

<span data-ttu-id="d0d36-119">W przypadku aplikacji przeznaczonych dla .NET Framework 4.6.2 lub nowszych te zmiany są domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="d0d36-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="d0d36-120">Powinny one zwiększyć wydajność, jednocześnie umożliwiając metodom dostęp do wcześniej niedostępnych ścieżek.</span><span class="sxs-lookup"><span data-stu-id="d0d36-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="d0d36-121">Ta zmiana nie wpłynie na aplikacje, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych wersji, ale działają na .NET Framework 4.6.2 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="d0d36-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d0d36-122">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="d0d36-122">Mitigation</span></span>  
 <span data-ttu-id="d0d36-123">Aplikacje przeznaczone dla .NET Framework 4.6.2 lub nowszych mogą zrezygnować z tej zmiany i użyć starszej normalizacji, dodając następujący element do [ \<> środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d0d36-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="d0d36-124">Aplikacje, które są przeznaczone dla .NET Framework 4.6.1 lub wcześniejszych, ale działają na .NET Framework 4.6.2 lub później, mogą umożliwić zmianę normalizacji ścieżki, dodając następujący wiersz do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) aplikacji. Konfiguracja rozszerzeniem</span><span class="sxs-lookup"><span data-stu-id="d0d36-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0d36-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0d36-125">See also</span></span>

- [<span data-ttu-id="d0d36-126">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="d0d36-126">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
