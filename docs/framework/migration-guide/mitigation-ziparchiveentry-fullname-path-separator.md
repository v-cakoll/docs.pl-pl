---
title: 'Środki zaradcze: ZipArchiveEntry.FullName Path Separator'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 908ac7c441dbb7f6c70b9fafc701d403fc153222
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251075"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="393f4-102">Środki zaradcze: ZipArchiveEntry.FullName Path Separator</span><span class="sxs-lookup"><span data-stu-id="393f4-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="393f4-103">Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.1 separatora ścieżki używany w <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwość zmienił się od ukośnika ("\\") używane w poprzednich wersjach programu .NET Framework w celu ukośnika ("/").</span><span class="sxs-lookup"><span data-stu-id="393f4-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="393f4-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> obiekty są tworzone przez wywołanie metody jednego z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="393f4-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="393f4-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="393f4-105">Impact</span></span>  
 <span data-ttu-id="393f4-106">Zmiana zapewnia implementacji .NET do zgodności z sekcji 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i umożliwia. Archiwa ZIP można dekompresja w systemach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="393f4-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="393f4-107">Podczas dekompresowania pliku zip, utworzone przez aplikację przeznaczonego poprzedniej wersji programu .NET Framework w systemach operacyjnych innych niż Windows, takich jak Macintosh nie powiedzie się, aby zachować strukturę katalogów.</span><span class="sxs-lookup"><span data-stu-id="393f4-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="393f4-108">Na przykład w przypadku komputerów Macintosh tworzy zbiór plików, których nazwy łączy ścieżki katalogu, wraz z dowolnym ukośnika odwrotnego ("\\") znaki i nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="393f4-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="393f4-109">W rezultacie struktura katalogów zdekompresowanych plików nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="393f4-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="393f4-110">Wpływ tej zmiany na. Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w programie .NET Framework <xref:System.IO> przestrzenią nazw powinna być minimalny, ponieważ te interfejsy API bezproblemowo może obsługiwać ukośnika ("/") lub ukośnika odwrotnego ("\\") jako znaku separatora ścieżki.</span><span class="sxs-lookup"><span data-stu-id="393f4-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="393f4-111">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="393f4-111">Mitigation</span></span>  
 <span data-ttu-id="393f4-112">Jeśli to zachowanie jest niepożądany, można zrezygnować z przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="393f4-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="393f4-113">Poniżej pokazano oba `<runtime>` sekcji i przełącznik zgody.</span><span class="sxs-lookup"><span data-stu-id="393f4-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="393f4-114">Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w programie .NET Framework 4.6.1 i nowszych wersjach zgodzić się na to zachowanie przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcja pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="393f4-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="393f4-115">Poniżej pokazano oba `<runtime>` sekcji i przełącznik opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="393f4-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="393f4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="393f4-116">See also</span></span>

- [<span data-ttu-id="393f4-117">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="393f4-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="393f4-118">Zgodność aplikacji w wersji 4.6.1</span><span class="sxs-lookup"><span data-stu-id="393f4-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
