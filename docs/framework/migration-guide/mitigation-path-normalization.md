---
title: 'Środki zaradcze: Normalizacja ścieżki'
description: Dowiedz się, jak zmieniono metodę normalizacji ścieżki w .NET Framework, zaczynając od aplikacji docelowych .NET Framework 4.6.2.
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 89dcc46d9f266ffd3635dc0cc02b634720356eda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475219"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="5b6f3-103">Środki zaradcze: Normalizacja ścieżki</span><span class="sxs-lookup"><span data-stu-id="5b6f3-103">Mitigation: Path Normalization</span></span>
<span data-ttu-id="5b6f3-104">Począwszy od aplikacji przeznaczonych do .NET Framework 4.6.2, normalizacja ścieżki w .NET Framework została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-104">Starting with apps that target .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="5b6f3-105">Co to jest normalizacja ścieżki?</span><span class="sxs-lookup"><span data-stu-id="5b6f3-105">What is path normalization?</span></span>  
 <span data-ttu-id="5b6f3-106">Normalizowanie ścieżki polega na zmodyfikowaniu ciągu, który identyfikuje ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-106">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="5b6f3-107">Normalizacja zazwyczaj obejmuje:</span><span class="sxs-lookup"><span data-stu-id="5b6f3-107">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="5b6f3-108">Separatory składników formę kanoniczną działa i katalogów.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-108">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="5b6f3-109">Zastosowanie bieżącego katalogu do ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-109">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="5b6f3-110">Ocenianie katalogu względnego ( `.` ) lub katalogu nadrzędnego ( `..` ) w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-110">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="5b6f3-111">Przycinanie określonych znaków.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-111">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="5b6f3-112">Zmiany</span><span class="sxs-lookup"><span data-stu-id="5b6f3-112">The changes</span></span>  
 <span data-ttu-id="5b6f3-113">Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, normalizacja ścieżki zmieniła się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5b6f3-113">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="5b6f3-114">Środowisko uruchomieniowe odkłada do funkcji [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) systemu operacyjnego, aby znormalizować ścieżki.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-114">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="5b6f3-115">Normalizacja nie obejmuje już przecinania końców segmentów katalogów (takich jak spacja na końcu nazwy katalogu).</span><span class="sxs-lookup"><span data-stu-id="5b6f3-115">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="5b6f3-116">Obsługa składni ścieżki urządzenia w pełnym zaufaniu, w tym `\\.\` i dla interfejsów API we/wy plików w mscorlib.dll, `\\?\` .</span><span class="sxs-lookup"><span data-stu-id="5b6f3-116">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="5b6f3-117">Środowisko uruchomieniowe nie sprawdza poprawności ścieżek składni urządzeń.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-117">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="5b6f3-118">Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-118">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5b6f3-119">Wpływ</span><span class="sxs-lookup"><span data-stu-id="5b6f3-119">Impact</span></span>  

<span data-ttu-id="5b6f3-120">W przypadku aplikacji przeznaczonych dla .NET Framework 4.6.2 lub nowszych te zmiany są domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-120">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="5b6f3-121">Powinny one zwiększyć wydajność, jednocześnie umożliwiając metodom dostęp do wcześniej niedostępnych ścieżek.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-121">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="5b6f3-122">Ta zmiana nie wpłynie na aplikacje, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych wersji, ale działają na .NET Framework 4.6.2 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="5b6f3-122">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5b6f3-123">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="5b6f3-123">Mitigation</span></span>  
 <span data-ttu-id="5b6f3-124">Aplikacje przeznaczone dla .NET Framework 4.6.2 lub nowszych mogą zrezygnować z tej zmiany i użyć starszej normalizacji, dodając następujący element do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="5b6f3-124">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="5b6f3-125">Aplikacje, które są przeznaczone dla .NET Framework 4.6.1 lub wcześniejszych, ale działają na .NET Framework 4.6.2 lub później, mogą umożliwić zmianę normalizacji ścieżki, dodając następujący wiersz do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="5b6f3-125">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b6f3-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b6f3-126">See also</span></span>

- [<span data-ttu-id="5b6f3-127">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="5b6f3-127">Application compatibility</span></span>](application-compatibility.md)
