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
ms.openlocfilehash: ea7c85e956828e918e3cfe205b980e543e257eb4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743956"
---
# <a name="shadow-copying-assemblies"></a>Kopiowanie zestawów w tle
Włącza zestawy, które są używane w domenie aplikacji do zaktualizowania bez zwalniania domeny aplikacji kopiowania w tle. Jest to szczególnie przydatne w przypadku aplikacji, które muszą być dostępne w sposób ciągły, takie jak lokacje programu ASP.NET.  
  
> [!IMPORTANT]
>  Kopiowanie w tle nie jest obsługiwany w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 Środowisko uruchomieniowe języka wspólnego blokuje pliku zestawu, gdy zestaw jest załadowany, więc nie można zaktualizować pliku, dopóki nie zostanie zwolniony zestawu. Zwalnianie domen aplikacji jest jedynym sposobem, aby zwolnić zestaw z domeny aplikacji, więc w normalnych okolicznościach zestawu nie można zaktualizować na dysku do wszystkich domen aplikacji, które korzystają z zostały usunięte.  
  
 Domeny aplikacji skonfigurowano do plików kopii w tle, zestawy w ścieżce aplikacji są skopiowany do innej lokalizacji i załadować z tej lokalizacji. Kopia jest zablokowany, ale oryginalny plik zestawu jest odblokowany i można go zaktualizować.  
  
> [!IMPORTANT]
>  Tylko zestawy, które mogą być kopie w tle są te są przechowywane w katalogu aplikacji lub jego podkatalogach, określony przez <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> właściwości po skonfigurowaniu domeny aplikacji. Zestawy przechowywanych w pamięci podręcznej GAC nie są kopie w tle.  
  
 Ten artykuł zawiera następujące sekcje:  
  
-   [Włączanie i przy użyciu kopiowanie w tle](#EnablingAndUsing) opisano podstawowe wykorzystanie i opcje, które są dostępne do kopiowania w tle.  
  
-   [Wydajność uruchamiania](#StartupPerformance) opisano zmiany wprowadzone do kopiowania w tle [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] w celu zwiększenia wydajności uruchamiania i jak przywrócić zachowanie starszych wersji.  
  
-   [Przestarzałe metody](#ObsoleteMethods) opisano zmiany, które zostały wprowadzone do właściwości i metod tego formantu kopiowanie w tle w [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)].  
  
<a name="EnablingAndUsing"></a>   
## <a name="enabling-and-using-shadow-copying"></a>Włączanie i korzystanie z kopiowania w tle  
 Można użyć właściwości <xref:System.AppDomainSetup> klasy w następujący sposób, aby skonfigurować domenę aplikacji do kopiowania w tle:  
  
-   Kopiowanie przez ustawienie w tle Włącz <xref:System.AppDomainSetup.ShadowCopyFiles%2A> wartość ciągu dla właściwości `"true"`.  
  
     Domyślnie to ustawienie powoduje wszystkie zestawy w ścieżce aplikacji ma zostać skopiowany do pamięci podręcznej pobierania przed załadowaniem. To jest tej samej pamięci podręcznej obsługiwanego przez środowisko uruchomieniowe języka wspólnego do przechowywania plików pobranych z innych komputerów, a środowisko uruchomieniowe języka wspólnego automatycznie usuwa pliki, gdy nie są już potrzebne.  
  
-   Opcjonalnie ustawić niestandardową lokalizację plików w tle przy użyciu <xref:System.AppDomainSetup.CachePath%2A> właściwości i <xref:System.AppDomainSetup.ApplicationName%2A> właściwości.  
  
     Podstawowa ścieżka lokalizacji jest tworzony przez łączenie <xref:System.AppDomainSetup.ApplicationName%2A> właściwości <xref:System.AppDomainSetup.CachePath%2A> właściwość jako podkatalogu. Zestawy są kopiowane do podkatalogów tej ścieżki nie do podstawowej sama ścieżka cień.  
  
    > [!NOTE]
    >  Jeśli <xref:System.AppDomainSetup.ApplicationName%2A> nie ustawiono właściwości <xref:System.AppDomainSetup.CachePath%2A> właściwości jest ignorowany i jest używany przez pamięć podręczną pobierania. Nie wyjątek.  
  
     Jeśli określisz lokalizacji niestandardowej, są zobowiązani do czyszczenia katalogów i skopiować pliki, kiedy nie są już potrzebne. Nie są automatycznie usuwane.  
  
     Istnieje kilka przyczyn, dlaczego warto ustawić niestandardową lokalizację plików w tle. Można ustawić niestandardową lokalizację plików w tle, jeśli aplikacja generuje dużą liczbę kopii. Pamięć podręczną pobierania jest ograniczona przez rozmiar, a nie przez okres istnienia, więc jest to możliwe, że środowisko uruchomieniowe języka wspólnego będzie próbował usunąć plik, który jest używany. Kolejny powód, aby ustawić niestandardową lokalizację jest w przypadku korzystania z aplikacji nie ma prawa do zapisu na lokalizację katalogu, środowisko uruchomieniowe języka wspólnego używanych przez pamięć podręczną pobierania.  
  
-   Opcjonalnie ograniczyć zestawy, które są w tle przy użyciu <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> właściwości.  
  
     Po włączeniu kopiowanie w tle dla domeny aplikacji, wartość domyślna to można skopiować wszystkie zestawy w ścieżce aplikacji — to znaczy w katalogach określony przez <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> właściwości. Można ograniczyć kopiowanie do wybranych katalogów, tworząc ciąg, który zawiera tylko katalogi chcesz kopii w tle i przypisywanie ciąg do <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> właściwości. Katalogi należy rozdzielić średnikami. Tylko zestawy, które są kopie w tle są pokazane w wybranych katalogów.  
  
    > [!NOTE]
    >  Jeśli nie przypisuj ciąg <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> właściwości, lub jeśli ta właściwość jest ustawiona na `null`, wszystkie zestawy w katalogach określonych przez <xref:System.AppDomainSetup.ApplicationBase%2A> i <xref:System.AppDomainSetup.PrivateBinPath%2A> właściwości są kopie w tle.  
  
    > [!IMPORTANT]
    >  Ponieważ średnik jest znak ogranicznika średnikami, nie może zawierać ścieżki katalogu. Brak nie znak ucieczki dla średnikami.  
  
<a name="StartupPerformance"></a>   
## <a name="startup-performance"></a>Startowa wydajność  
 Po uruchomieniu domeny aplikacji, która używa kopiowanie w tle, istnieje opóźnienie podczas zestawy w katalogu aplikacji są kopiowane do katalogu kopii w tle lub sprawdzić, czy są już w tej lokalizacji. Przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], wszystkie zestawy zostały skopiowane do katalogu tymczasowego. Otwarto każdego zestawu, aby zweryfikować nazwę zestawu, a silnej nazwy zostało zweryfikowane. Każdy zestaw zaznaczono czy miał został zaktualizowany niedawno niż kopia w tle kopii katalogu. Jeśli tak, został skopiowany do katalogu kopii w tle. Na koniec tymczasowe kopie zostały odrzucone.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], domyślne zachowanie uruchamiania jest bezpośrednie porównanie pliku Data i godzina każdego zestawu w katalogu aplikacji przy użyciu pliku daty i czasu kopii w tle katalogu kopii. Jeśli zestaw został zaktualizowany, jest kopiowana za pomocą tej samej procedury, jak w starszych wersjach programu .NET Framework; w przeciwnym razie kopia w tle kopii katalogu została załadowana.  
  
 Wynikowa zwiększenie wydajności jest największy dla aplikacji, w których zestawy nie zmieniają się często i zmiany zwykle występują w małego podzbioru zestawów. Większość zestawów w przypadku zmiany aplikacji są często używane nowe zachowanie domyślne może spowodować regresji wydajności. Można przywrócić zachowanie uruchamiania poprzednich wersji programu .NET Framework, dodając [ \<shadowCopyVerifyByTimestamp > element](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) do pliku konfiguracji z `enabled="false"`.  
  
<a name="ObsoleteMethods"></a>   
## <a name="obsolete-methods"></a>Metody przestarzałe  
 <xref:System.AppDomain> Klasa ma kilka metod, takich jak <xref:System.AppDomain.SetShadowCopyFiles%2A> i <xref:System.AppDomain.ClearShadowCopyPath%2A>, który może służyć do kontrolowania kopiowanie w tle w domenie aplikacji, ale te zostały oznaczone jako przestarzałe w programie .NET Framework w wersji 2.0. Zalecanym sposobem konfigurowania domeny aplikacji dla kopiowanie w tle jest użycie właściwości <xref:System.AppDomainSetup> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>  
 [\<shadowCopyVerifyByTimestamp > — Element](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
