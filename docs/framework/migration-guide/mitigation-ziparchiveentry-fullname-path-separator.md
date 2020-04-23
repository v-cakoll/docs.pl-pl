---
title: 'Łagodzenie: ZipArchiveEntry.FullName Separator ścieżki'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 3f6c7f258fd5dbf01db4d79b73b88ddd7484f9b2
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102622"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="b6e09-102">Łagodzenie: ZipArchiveEntry.FullName Separator ścieżki</span><span class="sxs-lookup"><span data-stu-id="b6e09-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="b6e09-103">Począwszy od aplikacji, które są przeznaczone dla programu .NET Framework 4.6.1, separator ścieżki używany we <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości został zmieniony z ukośnika odwrotnego ("\\") używanego w poprzednich wersjach programu .NET Framework na ukośnik do przodu ("/").</span><span class="sxs-lookup"><span data-stu-id="b6e09-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="b6e09-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywołanie jednego <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> z przeciążeń metody.</span><span class="sxs-lookup"><span data-stu-id="b6e09-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b6e09-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="b6e09-105">Impact</span></span>  
 <span data-ttu-id="b6e09-106">Zmiana wprowadza implementację platformy .NET w zgodność z sekcją 4.4.17.1 . [ Zip File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i pozwala . Zip archiwów do dekompresji w systemach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="b6e09-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="b6e09-107">Dekompresji pliku zip utworzonego przez aplikację, która jest przeznaczona dla poprzedniej wersji programu .NET Framework w systemach operacyjnych innych niż Windows, takich jak MacOS, nie można zachować struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="b6e09-107">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="b6e09-108">Na przykład w systemie MacOS tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wszelkie znaki ukośnika odwrotnego ("\\") i nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="b6e09-108">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="b6e09-109">W rezultacie struktura katalogów zdekompresowanych plików nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="b6e09-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="b6e09-110">Wpływ tej zmiany na . Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w obszarze nazw programu .NET Framework <xref:System.IO> powinny być minimalne,\\ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (" ") jako znak separatora ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b6e09-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b6e09-111">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="b6e09-111">Mitigation</span></span>  
 <span data-ttu-id="b6e09-112">Jeśli to zachowanie jest niepożądane, można zrezygnować, dodając [ \<](../configure-apps/file-schema/runtime/runtime-element.md) ustawienie konfiguracji do środowiska wykonawczego>sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6e09-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="b6e09-113">Poniżej przedstawiono `<runtime>` zarówno sekcję, jak i przełącznik rezygnacji.</span><span class="sxs-lookup"><span data-stu-id="b6e09-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="b6e09-114">Ponadto aplikacje przeznaczone dla poprzednich wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.6.1 i nowszych wersjach, mogą zdecydować się na to zachowanie, dodając ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6e09-114">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="b6e09-115">Poniżej przedstawiono `<runtime>` zarówno sekcję, jak i przełącznik opt-in.</span><span class="sxs-lookup"><span data-stu-id="b6e09-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6e09-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6e09-116">See also</span></span>

- [<span data-ttu-id="b6e09-117">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="b6e09-117">Application compatibility</span></span>](application-compatibility.md)
