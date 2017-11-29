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
ms.openlocfilehash: 36af59772418f5622d411f9df843f5dcd296be13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Ograniczenie: Ścieżka ZipArchiveEntry.FullName separatora
Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], separatora ścieżki używany w <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości zmienił się od ukośnika odwrotnego ("\\") używane w poprzednich wersjach programu .NET Framework do ukośnika ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywoływanie jednej z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Wpływ  
 Zmiana powoduje implementacji .NET do zgodności z sekcji 4.4.17.1 [. Specyfikacją formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i umożliwia. Archiwa ZIP do można zdekompresować w systemach z systemem innym niż Windows.  
  
 Podczas dekompresowania pliku zip utworzonego przez aplikację którego element docelowy poprzedniej wersji programu .NET Framework w systemach operacyjnych z systemem innym niż Windows, takich jak Macintosh nie powiedzie się, aby zachować struktura katalogów. Na przykład w przypadku komputerów Macintosh tworzy zestaw plików, których nazwy łączy ścieżki katalogu, wraz z dowolnym ukośnika odwrotnego ("\\") znaków, a nazwa pliku. W związku z tym struktura katalogów zdekompresowanych plików nie są zachowywane.  
  
 Wpływ tej zmiany na. Pliki ZIP, które są zdekompresować w systemie operacyjnym Windows przez interfejs API programu .NET Framework <xref:System.IO> przestrzeń nazw powinna mieć minimalny, ponieważ te interfejsy API bezproblemowo może obsłużyć ukośnika ("/") ani ukośnika odwrotnego ("\\") jako znaku separatora ścieżki.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli to zachowanie jest niepożądane, można zrezygnować z przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji. Poniżej pokazano zarówno `<runtime>` sekcji i przełącznik rezygnacji z.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ponadto aplikacje docelowe poprzednie wersje programu .NET Framework, które są uruchomione na [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i nowszych wersjach zgodzić się na to zachowanie przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji plik konfiguracji aplikacji. Poniżej pokazano zarówno `<runtime>` sekcji i przycisk akceptacji.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 [Zgodność aplikacji w wersji 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
