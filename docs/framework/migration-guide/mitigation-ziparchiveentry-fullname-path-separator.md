---
title: 'Środki zaradcze: separator ścieżki klasy ZipArchiveEntry. FullName'
description: Dowiedz się, w jaki sposób separator ścieżki dla właściwości ZipArchiveEntry. FullName został zmieniony, rozpoczynając od aplikacji, które są przeznaczone dla .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475297"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="24835-103">Środki zaradcze: separator ścieżki klasy ZipArchiveEntry. FullName</span><span class="sxs-lookup"><span data-stu-id="24835-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="24835-104">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, separator ścieżki używany we <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> Właściwości został zmieniony z ukośnika odwrotnego (" \\ ") użytego w poprzednich wersjach .NET Framework do ukośnika ("/").</span><span class="sxs-lookup"><span data-stu-id="24835-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="24835-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywołanie jednego z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="24835-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="24835-106">Wpływ</span><span class="sxs-lookup"><span data-stu-id="24835-106">Impact</span></span>  
 <span data-ttu-id="24835-107">Zmiana powoduje, że implementacja platformy .NET jest zgodna z sekcją 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i zezwala na to. Archiwa ZIP do skompresowania w systemach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="24835-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="24835-108">Dekompresowanie pliku zip utworzonego przez aplikację, która jest przeznaczona dla starszej wersji .NET Framework w systemach operacyjnych innych niż Windows, takich jak MacOS, nie można zachować struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="24835-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="24835-109">Na przykład w programie MacOS tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wszystkie znaki ukośnika odwrotnego (" \\ ") i nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="24835-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="24835-110">W związku z tym struktura katalogów nieskompresowanych plików nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="24835-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="24835-111">Wpływ tej zmiany na. Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w .NET Framework <xref:System.IO> przestrzeni nazw powinny być minimalne, ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (" \\ ") jako znak separatora ścieżki.</span><span class="sxs-lookup"><span data-stu-id="24835-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="24835-112">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="24835-112">Mitigation</span></span>  
 <span data-ttu-id="24835-113">Jeśli takie zachowanie jest niepożądane, można zrezygnować z dodania ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24835-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="24835-114">Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik rezygnacji.</span><span class="sxs-lookup"><span data-stu-id="24835-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="24835-115">Ponadto aplikacje przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 i nowszych wersjach mogą zrezygnować z tego zachowania przez dodanie ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24835-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="24835-116">Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik zgody.</span><span class="sxs-lookup"><span data-stu-id="24835-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24835-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24835-117">See also</span></span>

- [<span data-ttu-id="24835-118">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="24835-118">Application compatibility</span></span>](application-compatibility.md)
