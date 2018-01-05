---
title: "Ograniczenie: Ścieżka ZipArchiveEntry.FullName separatora"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ca43e4952f7ff457cf61c2c36334ab6213e50ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="95f9d-102">Ograniczenie: Ścieżka ZipArchiveEntry.FullName separatora</span><span class="sxs-lookup"><span data-stu-id="95f9d-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="95f9d-103">Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], separatora ścieżki używany w <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości zmienił się od ukośnika odwrotnego ("\\") używane w poprzednich wersjach programu .NET Framework do ukośnika ("/").</span><span class="sxs-lookup"><span data-stu-id="95f9d-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="95f9d-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywoływanie jednej z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="95f9d-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="95f9d-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="95f9d-105">Impact</span></span>  
 <span data-ttu-id="95f9d-106">Zmiana powoduje implementacji .NET do zgodności z sekcji 4.4.17.1 [. Specyfikacją formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i umożliwia. Archiwa ZIP do można zdekompresować w systemach z systemem innym niż Windows.</span><span class="sxs-lookup"><span data-stu-id="95f9d-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="95f9d-107">Podczas dekompresowania pliku zip utworzonego przez aplikację którego element docelowy poprzedniej wersji programu .NET Framework w systemach operacyjnych z systemem innym niż Windows, takich jak Macintosh nie powiedzie się, aby zachować struktura katalogów.</span><span class="sxs-lookup"><span data-stu-id="95f9d-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="95f9d-108">Na przykład w przypadku komputerów Macintosh tworzy zestaw plików, których nazwy łączy ścieżki katalogu, wraz z dowolnym ukośnika odwrotnego ("\\") znaków, a nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="95f9d-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="95f9d-109">W związku z tym struktura katalogów zdekompresowanych plików nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="95f9d-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="95f9d-110">Wpływ tej zmiany na. Pliki ZIP, które są zdekompresować w systemie operacyjnym Windows przez interfejs API programu .NET Framework <xref:System.IO> przestrzeń nazw powinna mieć minimalny, ponieważ te interfejsy API bezproblemowo może obsłużyć ukośnika ("/") ani ukośnika odwrotnego ("\\") jako znaku separatora ścieżki.</span><span class="sxs-lookup"><span data-stu-id="95f9d-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="95f9d-111">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="95f9d-111">Mitigation</span></span>  
 <span data-ttu-id="95f9d-112">Jeśli to zachowanie jest niepożądane, można zrezygnować z przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95f9d-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="95f9d-113">Poniżej pokazano zarówno `<runtime>` sekcji i przełącznik rezygnacji z.</span><span class="sxs-lookup"><span data-stu-id="95f9d-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="95f9d-114">Ponadto aplikacje docelowe poprzednie wersje programu .NET Framework, które są uruchomione na [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i nowszych wersjach zgodzić się na to zachowanie przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95f9d-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="95f9d-115">Poniżej pokazano zarówno `<runtime>` sekcji i przycisk akceptacji.</span><span class="sxs-lookup"><span data-stu-id="95f9d-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95f9d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95f9d-116">See Also</span></span>  
 [<span data-ttu-id="95f9d-117">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="95f9d-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 [<span data-ttu-id="95f9d-118">Zgodność aplikacji w wersji 4.6.1</span><span class="sxs-lookup"><span data-stu-id="95f9d-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
