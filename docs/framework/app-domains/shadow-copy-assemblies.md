---
title: Kopiowanie zestawów w tle
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51bf359ea6ba4e5b45827928a50a095a7960a68f
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456711"
---
# <a name="shadow-copying-assemblies"></a>Kopiowanie zestawów w tle
Kopiowanie zestawów umożliwia, które są używane w domenie aplikacji, należy zaktualizować bez rozładowywania domeny aplikacji w tle. Jest to szczególnie przydatne w przypadku aplikacji, które muszą być dostępne w sposób ciągły, takich jak witryny programu ASP.NET.  
  
> [!IMPORTANT]
>  Kopiowanie w tle nie jest obsługiwane w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 Środowisko uruchomieniowe języka wspólnego blokuje plik zestawu, gdy zestaw jest ładowany, więc nie można zaktualizować pliku, dopóki nie zostanie zwolniony zestawu. Jedynym sposobem, aby zwolnić zestaw z domeny aplikacji jest rozładowywania domeny aplikacji, dzięki czemu w normalnych warunkach, dopóki wszystkie domeny aplikacji, które korzystają z zestawu nie można zaktualizować na dysku zostały usunięte.  
  
 Gdy domeny aplikacji jest skonfigurowany do plików kopii w tle, zestawów w ścieżce aplikacji są kopiowany do innej lokalizacji i załadować z tej lokalizacji. Kopia jest zablokowany, ale oryginalny plik zestawu jest odblokowana i może zostać zaktualizowany.  
  
> [!IMPORTANT]
>  Tylko zestawy, które mogą być kopiowane w tle są te, przechowywane w katalogu aplikacji lub jego podkatalogów określonego przez <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> właściwości, gdy jest skonfigurowana w domenie aplikacji. Zestawów przechowywanej w globalnej pamięci podręcznej nie są kopiowane w tle.  
  
 Ten artykuł zawiera następujące sekcje:  
  
- [Włączanie i kopiowania w tle za pomocą](#EnablingAndUsing) w tym artykule opisano podstawowe zastosowanie i opcje, które są dostępne dla kopiowania w tle.  
  
- [Startowa wydajność](#StartupPerformance) w tym artykule opisano zmiany wprowadzone do kopiowania w tle [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Aby zwiększyć wydajność uruchamiania i jak przywrócić działanie wcześniejszych wersji.  
  
- [Metody przestarzałe](#ObsoleteMethods) w tym artykule opisano zmiany, które zostały wprowadzone do właściwości i metod tego formantu kopiowanie w tle w [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)].  
  
<a name="EnablingAndUsing"></a>   
## <a name="enabling-and-using-shadow-copying"></a>Włączanie i korzystanie z kopiowania w tle  
 Można użyć właściwości <xref:System.AppDomainSetup> klasy w następujący sposób, aby skonfigurować domenę aplikacji do kopiowania w tle:  
  
- Kopiowanie, ustawiając w tle Włącz <xref:System.AppDomainSetup.ShadowCopyFiles%2A> właściwości do wartości ciągu `"true"`.  
  
     Domyślnie to ustawienie powoduje, że wszystkie zestawy ścieżka aplikacji, które mają być kopiowane do pamięci podręcznej pobierania, przed załadowaniem. Jest tej samej pamięci podręcznej, obsługiwane przez środowisko uruchomieniowe języka wspólnego do przechowywania plików pobranych z innych komputerów i środowiska uruchomieniowego języka wspólnego automatycznie usuwa pliki, gdy nie są już potrzebne.  
  
- Opcjonalnie ustaw niestandardową lokalizację plików kopie w tle za pomocą <xref:System.AppDomainSetup.CachePath%2A> właściwości i <xref:System.AppDomainSetup.ApplicationName%2A> właściwości.  
  
     Podstawowa ścieżka lokalizacji jest tworzona przez złączenie <xref:System.AppDomainSetup.ApplicationName%2A> właściwość <xref:System.AppDomainSetup.CachePath%2A> właściwość jako podkatalogu. Zestawy są kopiowane do podkatalogów tej ścieżki, aby sama ścieżka podstawowa nie w tle.  
  
    > [!NOTE]
    >  Jeśli <xref:System.AppDomainSetup.ApplicationName%2A> nie ustawiono właściwości <xref:System.AppDomainSetup.CachePath%2A> właściwość jest ignorowana, a pamięć podręczna pobierania jest używana. Jest zgłaszany żaden wyjątek.  
  
     Jeśli określisz niestandardową lokalizację, jest odpowiedzialny za czyszczenie katalogów i skopiować pliki, gdy nie są już potrzebne. Nie są automatycznie usuwane.  
  
     Istnieje kilka powodów dlaczego warto ustawić niestandardową lokalizację plików kopie w tle. Można ustawić niestandardową lokalizację plików kopie w tle, jeśli aplikacja generuje dużą liczbę kopii. Pamięć podręczna pobierania jest ograniczona przez rozmiar, a nie przez okres istnienia, więc jest możliwe, że środowisko uruchomieniowe języka wspólnego podejmie próbę usunięcia pliku, który jest używany. Kolejny powód, aby ustawić niestandardową lokalizację jest, gdy użytkownicy korzystający z aplikacji nie mieć dostęp do zapisu na lokalizację katalogu, w której środowisko uruchomieniowe języka wspólnego używa pamięci podręcznej pobierania.  
  
- Opcjonalnie ogranicz zestawy, które są kopie w tle woluminów przy użyciu <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> właściwości.  
  
     Po włączeniu kopiowania w tle dla domeny aplikacji, wartość domyślna to do skopiowania wszystkich zestawów w ścieżce aplikacji — czyli w katalogi określone przez <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> właściwości. Można ograniczyć kopiowanie do wybranych katalogów, tworząc ciąg, który zawiera tylko te katalogi, które chcesz umieścić w kopii w tle i przypisywanie ciąg <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> właściwości. Katalogi należy oddzielić średnikami. Tylko zestawy, które są kopiowane w tle są pokazane w wybranych katalogów.  
  
    > [!NOTE]
    >  Jeśli nie przypiszesz ciąg <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> właściwości, lub jeśli ta właściwość jest ustawiona na `null`, wszystkie zestawy w katalogi określone przez <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> właściwości są kopie w tle.  
  
    > [!IMPORTANT]
    >  Ścieżek katalogów nie mogą zawierać średnikami, ponieważ znajduje się znak ogranicznika. Nie ma żadnych znak ucieczki dla średnikami.  
  
<a name="StartupPerformance"></a>   
## <a name="startup-performance"></a>Startowa wydajność  
 Po uruchomieniu domeny aplikacji, która używa kopiowania w tle występuje opóźnienie podczas zestawów w katalogu aplikacji są kopiowane do katalogu kopii w tle lub zweryfikować, czy są już w tej lokalizacji. Przed .NET Framework 4 wszystkie zestawy zostały skopiowane do katalogu tymczasowego. Każdy zestaw został otwarty, aby sprawdzić nazwę zestawu, a została zweryfikowana silnej nazwy. Każdy zestaw została sprawdzona czy miał został zaktualizowany niedawno kopiowania w katalogu kopii w tle. Jeśli tak, został skopiowany do katalogu kopii w tle. Na koniec tymczasowej kopii zostały odrzucone.  
  
 Począwszy od programu .NET Framework 4, domyślne zachowanie uruchamiania jest bezpośrednio porównanie pliku daty i czasu każdego zestawu w katalogu aplikacji z datą pliku oraz czasu kopiowania w katalogu kopii w tle. Jeśli zestaw został zaktualizowany, jest kopiowany przy użyciu tej samej procedury jak w starszych wersjach programu .NET Framework; w przeciwnym razie kopia w katalogu kopii w tle jest ładowany.  
  
 Wynikowy wzrost wydajności jest największy dla aplikacji, w których zestawy nie zmieniają się często, a zmiany są zazwyczaj występuje w mały podzbiór zestawów. Większość zestawów w zmiany aplikacji są często nowe zachowanie może spowodować regresji wydajności. Można przywrócić zachowanie uruchamiania z poprzednich wersji programu .NET Framework, dodając [ \<shadowCopyVerifyByTimestamp > element](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) do pliku konfiguracji z `enabled="false"`.  
  
<a name="ObsoleteMethods"></a>   
## <a name="obsolete-methods"></a>Metody przestarzałe  
 <xref:System.AppDomain> Klasa ma kilka metod, takich jak <xref:System.AppDomain.SetShadowCopyFiles%2A> i <xref:System.AppDomain.ClearShadowCopyPath%2A>, który może służyć do kontrolowania kopiowania w tle na domenę aplikacji, ale te zostały oznaczone jako przestarzałe w programie .NET Framework w wersji 2.0. Zalecanym sposobem konfigurowanie domeny aplikacji, w przypadku kopiowania w tle jest użycie właściwości <xref:System.AppDomainSetup> klasy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [\<shadowCopyVerifyByTimestamp > Element](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
