---
title: 'Łagodzenie: Normalizacja ścieżki'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181235"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="91f47-102">Łagodzenie: Normalizacja ścieżki</span><span class="sxs-lookup"><span data-stu-id="91f47-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="91f47-103">Począwszy od aplikacji docelowego .NET Framework 4.6.2, normalizacji ścieżki w .NET Framework została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="91f47-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="91f47-104">Co to jest normalizacja ścieżki?</span><span class="sxs-lookup"><span data-stu-id="91f47-104">What is path normalization?</span></span>  
 <span data-ttu-id="91f47-105">Normalizacja ścieżki polega na zmodyfikowaniu ciągu identyfikującego ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="91f47-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="91f47-106">Normalizacja zazwyczaj obejmuje:</span><span class="sxs-lookup"><span data-stu-id="91f47-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="91f47-107">Kanonizacja separatorów komponentów i katalogów.</span><span class="sxs-lookup"><span data-stu-id="91f47-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="91f47-108">Stosowanie bieżącego katalogu do ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="91f47-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="91f47-109">Ocena katalogu względnego`.`( ) lub katalogu`..`nadrzędnego ( ) w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="91f47-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="91f47-110">Przycinanie określonych znaków.</span><span class="sxs-lookup"><span data-stu-id="91f47-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="91f47-111">Zmiany</span><span class="sxs-lookup"><span data-stu-id="91f47-111">The changes</span></span>  
 <span data-ttu-id="91f47-112">Począwszy od aplikacji docelowych dla programu .NET Framework 4.6.2, normalizacja ścieżki zmieniła się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="91f47-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="91f47-113">Środowisko wykonawcze defers do systemu operacyjnego [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkcji do normalizacji ścieżek.</span><span class="sxs-lookup"><span data-stu-id="91f47-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="91f47-114">Normalizacja nie obejmuje już przycinania końca segmentów katalogów (na przykład spacji na końcu nazwy katalogu).</span><span class="sxs-lookup"><span data-stu-id="91f47-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="91f47-115">Obsługa składni ścieżki urządzenia w pełnym `\\.\` zaufaniu, w tym i dla interfejsów API we/wy pliku w pliku mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="91f47-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="91f47-116">Środowisko wykonawcze nie sprawdza poprawności ścieżek składni urządzenia.</span><span class="sxs-lookup"><span data-stu-id="91f47-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="91f47-117">Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.</span><span class="sxs-lookup"><span data-stu-id="91f47-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="91f47-118">Wpływ</span><span class="sxs-lookup"><span data-stu-id="91f47-118">Impact</span></span>  

<span data-ttu-id="91f47-119">W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.6.2 lub nowszego te zmiany są domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="91f47-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="91f47-120">Powinny one poprawić wydajność, umożliwiając jednocześnie metody dostępu wcześniej niedostępne ścieżki.</span><span class="sxs-lookup"><span data-stu-id="91f47-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="91f47-121">Aplikacje przeznaczone dla programu .NET Framework 4.6.1 i wcześniejszych wersji, ale są uruchomione w ramach .NET Framework 4.6.2 lub nowszej, nie mają wpływu na tę zmianę.</span><span class="sxs-lookup"><span data-stu-id="91f47-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="91f47-122">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="91f47-122">Mitigation</span></span>  
 <span data-ttu-id="91f47-123">Aplikacje przeznaczone dla programu .NET Framework 4.6.2 lub nowszego mogą zrezygnować z tej zmiany i używać normalizacji starszych, dodając następujące elementy do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="91f47-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="91f47-124">Aplikacje przeznaczone dla programu .NET Framework 4.6.1 lub starsze, ale działające w programie .NET Framework 4.6.2 lub nowszym, mogą włączyć zmiany w normalizacji ścieżki, dodając następujący wiersz do sekcji>środowiska [ \<wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="91f47-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91f47-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91f47-125">See also</span></span>

- [<span data-ttu-id="91f47-126">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="91f47-126">Application compatibility</span></span>](application-compatibility.md)
