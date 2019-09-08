---
title: Środki zaradcze ZipArchiveEntry.FullName Path Separator
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
ms.openlocfilehash: b97436ca2f81fea139689c7c2c2348718827b90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778866"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="ac5d6-102">Środki zaradcze ZipArchiveEntry.FullName Path Separator</span><span class="sxs-lookup"><span data-stu-id="ac5d6-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="ac5d6-103">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, separator ścieżki używany we <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości został zmieniony od ukośnika odwrotnego (\\"") użytego w poprzednich wersjach .NET Framework do ukośnika ("/").</span><span class="sxs-lookup"><span data-stu-id="ac5d6-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="ac5d6-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywołanie jednego z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ac5d6-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="ac5d6-105">Impact</span></span>  
 <span data-ttu-id="ac5d6-106">Zmiana powoduje, że implementacja platformy .NET jest zgodna z sekcją 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i zezwala na to. Archiwa ZIP do skompresowania w systemach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="ac5d6-107">Dekompresowanie pliku zip utworzonego przez aplikację, która jest przeznaczona dla starszej wersji .NET Framework w systemach operacyjnych innych niż Windows, takich jak Macintosh, nie można zachować struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="ac5d6-108">Na przykład w systemie Macintosh tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wraz z dowolnym znakiem ukośnika odwrotnego ("\\") i nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="ac5d6-109">W związku z tym struktura katalogów nieskompresowanych plików nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="ac5d6-110">Wpływ tej zmiany na. Pliki zip, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w przestrzeni <xref:System.IO> nazw .NET Framework powinny być minimalne, ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (\\"") jako znak separatora ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ac5d6-111">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="ac5d6-111">Mitigation</span></span>  
 <span data-ttu-id="ac5d6-112">Jeśli takie zachowanie jest niepożądane, można zrezygnować z dodania ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="ac5d6-113">Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik rezygnacji.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="ac5d6-114">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 i nowszych wersjach, mogą zrezygnować z tego zachowania poprzez dodanie ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) aplikacji plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="ac5d6-115">Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik zgody.</span><span class="sxs-lookup"><span data-stu-id="ac5d6-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac5d6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac5d6-116">See also</span></span>

- [<span data-ttu-id="ac5d6-117">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="ac5d6-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="ac5d6-118">Zgodność aplikacji w 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ac5d6-118">Application Compatibility in 4.6.1</span></span>](application-compatibility-in-the-net-framework-4-6-1.md)
