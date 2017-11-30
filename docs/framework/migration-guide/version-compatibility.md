---
title: "Zgodność wersji w programie .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 166d61339d2b74f378b50ade4b78fd41e9692f76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="version-compatibility-in-the-net-framework"></a>Zgodność wersji w programie .NET Framework
Zgodności z poprzednimi wersjami oznacza, że aplikacja, która została opracowana dla określonej wersji platformy będzie działać w nowszych wersjach tej platformy. Próbuje zmaksymalizować zgodności z poprzednimi wersjami programu .NET Framework: źródła kodu napisanego dla jednej wersji programu .NET Framework należy skompilować w nowszych wersjach programu .NET Framework i zachowania tak samo w przypadku plików binarnych, działających w jednej wersji programu .NET Framework nowsze wersje programu .NET Framework.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Kompatybilność wersji dla aplikacji  
 Domyślnie aplikacja jest uruchamiana w tej wersji programu .NET Framework, który został utworzony dla. Jeśli nie jest obecny i pliku konfiguracji aplikacji nie definiuje wersji, może wystąpić błąd inicjowania programu .NET Framework. W takim przypadku do uruchomienia aplikacji nie powiedzie się.  
  
 Aby zdefiniować określonych wersji, na których aplikacja będzie działać, należy dodać co najmniej jeden [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementy do pliku konfiguracji aplikacji. Każdy `<supportedRuntime>` element zawiera obsługiwaną wersję środowiska uruchomieniowego przy pierwszym określanie wersji najlepszy możliwy oraz za ostatni określanie wersji najmniej preferowanych.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie aplikacji do obsługi platformy .NET Framework 4 lub 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).  
  
## <a name="version-compatibility-for-components"></a>Kompatybilność wersji dla składników  
 Aplikację można kontrolować wersji programu .NET Framework, na którym działa, ale nie składnika. Składniki i biblioteki klas są ładowane w ramach danej aplikacji, a w związku z tym automatycznego uruchamiania na wersji programu .NET Framework, która aplikacja jest uruchamiana na.  
  
 Z powodu tego ograniczenia gwarancje zgodności są szczególnie istotne dla składników. Począwszy od programu .NET Framework 4, można określić stopień, do którego składnik oczekuje się w celu zachowania zgodności w różnych wersjach, stosując <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> atrybutu dla tego składnika. Narzędzia można użyć tego atrybutu, aby wykryć potencjalnych naruszeń zgodności gwarantuje w przyszłych wersjach składnika.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Zgodność z poprzednimi wersjami i .NET Framework 4.5  
 .NET Framework 4.5 lub nowszy jest zgodny z aplikacjami, które zostały utworzone we wcześniejszych wersjach programu .NET Framework. Innymi słowy aplikacje i składniki utworzone w poprzednich wersjach będzie działać bez żadnych modyfikacji w programie .NET Framework 4.5 lub nowszym. Domyślnie aplikacje uruchamiać na wersji środowiska CLR, dla którego zostały opracowane, więc musisz podać plik konfiguracji do włączenia aplikacji do uruchamiania na .NET Framework 4.5 lub nowszy. Aby uzyskać więcej informacji, zobacz [kompatybilność wersji dla aplikacji](#Apps) wcześniej w tym artykule.  
  
 W praktyce to zgodności można uszkodzony pozornie wpływu zmiany w .NET Framework i zmian w technik programowania. Lepsza wydajność programu .NET Framework 4.5 mogą na przykład ujawnić sytuacji wyścigu, które nie były wykonywane we wcześniejszych wersjach. Podobnie, przy użyciu ścieżki ustalony do zestawów platformy .NET Framework, wykonywanie porównanie równości z określoną wersją programu .NET Framework i pobierania wartości pola prywatnej przy użyciu odbicia nie są zapewniającej rozwiązania. Ponadto każda wersja programu .NET Framework obejmuje poprawki błędów i zmiany dotyczące zabezpieczeń, które mogą wpłynąć na zgodność niektóre aplikacje i składniki.  
  
 Jeśli aplikację lub składnik nie działa zgodnie z oczekiwaniami w .NET Framework 4.5 (łącznie z jego wersje punktu [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 lub 4.7.1, użyj poniższej listy kontrolne:  
  
-  Jeśli aplikacja został opracowany, aby uruchomić w dowolnej wersji systemu .NET Framework, począwszy od programu .NET Framework 4.0, zobacz [zgodność aplikacji w programie .NET Framework](application-compatibility.md) do wygenerowania listy zmian między sieci docelowej wersji .NET Framework i wersji, na którym jest uruchomiona aplikacja.  

- Jeśli masz aplikację .NET Framework 3.5, zobacz też [zagadnienia migracji programu .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md).

- Jeśli masz aplikację .NET Framework 2.0, zobacz też [zmiany w programie .NET Framework 3.5 z dodatkiem SP1](http://go.microsoft.com/fwlink/?LinkId=186989).

- Jeśli masz aplikację .NET Framework 1.1, zobacz też [zmiany w programie .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkID=125263).  
  
-   Jeśli są ponowną kompilację istniejącego kodu źródłowego do uruchamiania na .NET Framework 4.5 lub jego punktu wersjach lub jeśli tworzysz nową wersję aplikacji lub składnika, którego celem jest [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub jego punktu zwalnia z istniejących wyboru podstawowej, kod źródłowy [ Co to jest przestarzałe w bibliotece klas](../../../docs/framework/whats-new/whats-obsolete.md) przestarzałe typy i składniki oraz zastosowanie obejścia problemu opisanego. (Wcześniej skompilowany kod będzie nadal działać względem typów i elementów członkowskich, które zostały oznaczone jako przestarzałe.)  
  
-   Jeśli okaże się, że zmiany w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] uległ aplikację wyboru [schemat ustawień środowiska uruchomieniowego](../../../docs/framework/configure-apps/file-schema/runtime/index.md) ustalenie, czy umożliwia ustawienie środowiska uruchomieniowego w pliku konfiguracyjnym aplikacji Przywróć poprzednie.  
  
-   Jeśli napotkasz problem, który nie jest udokumentowany pliku [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) usterek i skontaktuj się z [ netfxcf@microsoft.com ](mailto:netfxcf@microsoft.com) numer błędu.  
  
## <a name="compatibility-and-side-by-side-execution"></a>Zgodność i side-by-side wykonywania  
 Jeśli nie można znaleźć odpowiedniego rozwiązania, opis problemu, należy pamiętać, że program .NET Framework 4.5 (lub jeden z jego wersje punktu) działa równolegle z wersji 1.1, 2.0 i 3.5 i jest dostępna aktualizacja w miejscu, które zastępuje w wersji 4. Dla aplikacji, które odnoszą się do wersji 1.1, 2.0 i 3.5 można zainstalować odpowiednią wersję programu .NET Framework na komputerze docelowym, aby uruchomić aplikację w jego najlepsze środowisko. Aby uzyskać więcej informacji na temat wykonywania side-by-side, zobacz [wykonywania Side-by-Side](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości](../../../docs/framework/whats-new/index.md)  
 [Co to jest przestarzałe w bibliotece klas](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Zgodność aplikacji](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Wsparcia technicznego produktów firmy Microsoft .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
 [Problemy dotyczące programu .NET framework 4 migracji](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
