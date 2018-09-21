---
title: Zgodność wersji w programie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d3d0e2dbd57d9581d1c8b0ca42d1e9d556d8905
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485629"
---
# <a name="version-compatibility-in-the-net-framework"></a>Zgodność wersji w programie .NET Framework
Zgodność ze starszymi wersjami oznacza, że aplikacja opracowana dla konkretnej wersji platformy będzie działać w nowszych wersjach tej platformy. .NET Framework próbuje maksymalizować zgodność ze starszymi wersjami: kod źródłowy napisany dla jednej wersji programu .NET Framework powinien kompilować się w nowszych wersjach .NET Framework i pliki binarne, które działają w jednej wersji programu .NET Framework powinien zachowują się identycznie w nowsze wersje programu .NET Framework.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Zgodność wersji aplikacji  
 Domyślnie aplikacja jest uruchamiana w wersji programu .NET Framework, która została skompilowana. Jeśli ta wersja nie jest obecny i pliku konfiguracji aplikacji nie definiuje obsługiwanych wersji, może wystąpić błąd inicjalizacji programu .NET Framework. W tym przypadku próba uruchomienia aplikacji nie powiedzie się.  
  
 Aby zdefiniować określonych wersji, na których dana aplikacja działa, Dodaj jeden lub kilka [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementy do pliku konfiguracji aplikacji. Każdy `<supportedRuntime>` element zawiera listę obsługiwanych wersji środowiska uruchomieniowego, przy czym pierwsze określenie najbardziej preferowaną wersję, a ostatni Określanie najmniej preferowaną wersję.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Konfiguracja aplikacji do obsługi platformy .NET Framework 4 lub 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).  
  
## <a name="version-compatibility-for-components"></a>Zgodność wersji składników  
 Aplikacja może kontrolować wersję .NET Framework, na którym działa, ale składnik nie może. Składniki biblioteki klas są ładowane w kontekście określonej aplikacji i dlatego automatycznie są uruchamiane w wersji programu .NET Framework, która jest uruchamiana aplikacja.  
  
 Ze względu na to ograniczenie gwarancje zgodności są szczególnie ważne dla składników. Począwszy od programu .NET Framework 4, można określić stopień, w jakim składnik powinien być zgodny w wielu wersjach, stosując <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> atrybutu do tego składnika. Narzędzia ten atrybut służy do wykrywania potencjalnych naruszeń zgodności gwarantuje w przyszłych wersjach składnika.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Zgodność ze starszymi wersjami a program .NET Framework 4.5  
 .NET Framework 4.5 i nowsze wersje są zgodne wstecz z aplikacjami, które zostały utworzone w starszych wersjach programu .NET Framework. Innymi słowy aplikacje i składniki utworzone w starszych wersjach będą działać bez żadnych modyfikacji na .NET Framework 4.5 lub nowszy. Jednak domyślnie aplikacje działają w wersjach środowiska CLR, dla którego zostały opracowane, więc może trzeba będzie podać plik konfiguracji, aby umożliwić aplikacji uruchamiania na .NET Framework 4.5 lub nowszy. Aby uzyskać więcej informacji, zobacz [zgodność wersji aplikacji](#Apps) sekcji we wcześniejszej części tego artykułu.  
  
 W praktyce tę zgodność można zaburzyć przez niekonsekwentne zmiany w .NET Framework i zmiany w technikach programowania. Ulepszenia wydajności w .NET Framework 4.5 można na przykład ujawnić wyścigu, która nie nastąpiła we wcześniejszych wersjach. Podobnie za pomocą ustalona ścieżka do zestawów .NET Framework, wykonywania porównania z określoną wersą .NET Framework i pobierania wartości pola prywatnego przy użyciu odbicia nie są praktykami zgodności z poprzednimi wersjami. Ponadto każda wersja programu .NET Framework zawiera poprawki i zmiany dotyczące zabezpieczeń, które mogą wpływać na zgodność niektórych aplikacji i składników.  
  
 Jeśli aplikacja lub składnik nie działa zgodnie z oczekiwaniami w .NET Framework 4.5 (łącznie z jego wydania punktowe, [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 lub 4.7.2, użyj poniższych list kontrolnych:  
  
-  Jeśli aplikacja została opracowana działają w dowolnej wersji programu .NET Framework, począwszy od programu .NET Framework 4.0, zobacz [zgodność aplikacji w programie .NET Framework](application-compatibility.md) do wygenerowania listy zmian między wersjami usługi wersję docelową .NET Framework i wersja, na którym uruchomiona jest aplikacja.  

- Jeśli masz aplikację .NET Framework 3.5, zobacz też [zagadnienia dotyczące migracji programu .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md).

- Jeśli masz aplikację .NET Framework 2.0, zobacz też [zmiany w .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkId=186989).

- Jeśli masz aplikację .NET Framework 1.1, zobacz też [zmiany w programie .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkID=125263).  
  
-   Jeśli rekompilujesz istniejący kod źródłowy do uruchamiania na .NET Framework 4.5 lub jego punktu wersji lub jeśli tworzysz nową wersję aplikacji lub składnika, który jest przeznaczony dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jego wydania punktowe z istniejącą podstawowej, kontrolę kodu źródłowego [ What's Obsolete in biblioteki klas](../../../docs/framework/whats-new/whats-obsolete.md) opis przestarzałych typów i członków i zastosuj opisane obejście. (Wcześniej skompilowany kod będzie wykonywany dla typów i członków, którzy zostali oznaczeni jako przestarzali.)  
  
-   Jeśli stwierdzisz, że zmiana [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zniszczyła aplikację, zajrzyj [schemat ustawień środowiska uruchomieniowego](../../../docs/framework/configure-apps/file-schema/runtime/index.md) do określenia, czy możesz użyć ustawienia środowiska uruchomieniowego w pliku konfiguracyjnym aplikacji, można przywrócić poprzednie zachowanie.  
  
-   Jeśli wystąpi problem, który nie jest udokumentowany, otwórz problem na [witrynę społeczność deweloperów rozwiązań dla platformy .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) lub Otwórz problem w [repozytorium GitHub Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).
  
## <a name="compatibility-and-side-by-side-execution"></a>Zgodność i side-by-side wykonywania  
 Jeśli nie możesz znaleźć odpowiedniego obejścia problemu, należy pamiętać, że działa równocześnie z wersjami 1.1, 2.0 i 3.5 programu .NET Framework 4.5 (lub jeden z jego wydania punktowe) i stanowi aktualizację w miejscu, która zastępuje wersję 4. W przypadku aplikacji przeznaczonych dla wersji 1.1, 2.0 i 3.5 można zainstalować odpowiednią wersję programu .NET Framework na komputerze docelowym, aby uruchomić aplikację w najlepszym środowisku. Aby uzyskać więcej informacji na temat wykonywania side-by-side zobacz [Side-by-Side Execution](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Co nowego](../../../docs/framework/whats-new/index.md)  
 [Przestarzałe elementy w ułatwieniach dostępu](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Zgodność aplikacji](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Cykl wsparcia technicznego dla programu Microsoft .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=248212)  
 [Zagadnienia dotyczące migracji programu .NET framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
