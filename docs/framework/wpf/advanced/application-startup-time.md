---
title: Czas uruchamiania aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- splash screen [WPF], startup time
- WPF [WPF], startup time
- startup time [WPF]
- application startup [WPF]
- performance [WPF], startup time
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
ms.openlocfilehash: 8452c41bc6d60d18fa058966299e3ca2b989604f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541953"
---
# <a name="application-startup-time"></a>Czas uruchamiania aplikacji
Ilość czasu wymaganego do uruchomienia aplikacji WPF mogą się znacznie różnić. W tym temacie opisano różne techniki skracanie czasu uruchamiania postrzegana i rzeczywistych dla aplikacji Windows Presentation Foundation (WPF).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Opis uruchamiania zimnych i ponowne uruchamianie  
 Uruchamianie zimnych występuje podczas uruchamiania aplikacji po raz pierwszy po ponownym uruchomieniu systemu lub podczas uruchamiania aplikacji, zamknij je, a następnie uruchom go ponownie po długim okresie. Podczas uruchamiania aplikacji, jeśli nie ma na liście oczekiwania menedżera pamięci systemu Windows wymagane stron (kod, dane statyczne, rejestru itp.), są wykonywane błędów stron. Dostęp do dysku jest wymagany do zapewnienia stron pamięci.  
  
 Ponowne uruchamianie występuje, gdy większość stron główne składniki środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego są już załadowane w pamięci, co pozwala zaoszczędzić czas dostępu do dysku kosztowne. Właśnie dlatego zarządzanej aplikacji rozpoczyna się szybciej, gdy jest uruchamiany po raz drugi.  
  
## <a name="implement-a-splash-screen"></a>Implementowanie ekranu powitalnego  
 W przypadkach, gdy jest znaczny, nieuniknione opóźnienie między uruchomieniem aplikacji oraz wyświetlanie pierwszego interfejsu użytkownika, optymalizacja czas uruchamiania postrzegana przy użyciu *ekranu powitalnego*. Ta metoda Wyświetla obraz niemal natychmiast po uruchomieniu aplikacji. Gdy aplikacja jest gotowa do wyświetlenia jej pierwszym interfejsu użytkownika, stopniowo ekranu powitalnego. Począwszy od [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], można użyć <xref:System.Windows.SplashScreen> klasy do zaimplementowania ekranu powitalnego. Aby uzyskać więcej informacji, zobacz [dodać ekranu powitalnego aplikacji WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Można też wdrożyć ekranu powitalnego za pomocą natywnego grafiki Win32. Wyświetlanie implementacji przed <xref:System.Windows.Application.Run%2A> metoda jest wywoływana.  
  
## <a name="analyze-the-startup-code"></a>Analizowanie kod uruchomienia  
 Określ przyczynę powolne początkowa zimnych. We/Wy dysku mogą być odpowiedzialne, ale nie zawsze jest wielkość liter. Ogólnie rzecz biorąc należy zminimalizować korzystanie z zasobów zewnętrznych, takich jak sieci, usług sieci Web lub na dysku.  
  
 Aby przetestować, należy sprawdzić, czy nie inne uruchomione aplikacje lub usługi użyć kodu zarządzanego lub kod WPF.  
  
 Uruchom natychmiast po ponownym uruchomieniu aplikacji WPF i określić, jak długo trwa do wyświetlenia. Jeśli wszystkie kolejne spowoduje uruchomienie aplikacji (ponowne uruchomienia) jest znacznie szybsze, problem uruchamiania zimnych najprawdopodobniej spowodowane przez operacje We/Wy.  
  
 Jeśli aplikacja zimnych problem uruchamiania nie jest powiązana z operacji We/Wy, istnieje duże prawdopodobieństwo, że aplikacja wykonuje niektóre długich inicjowania lub obliczeń, czeka na niektóre zdarzenia zakończyć, lub wymaga dużo kompilacji JIT podczas uruchamiania. W poniższych sekcjach opisano niektóre z tych sytuacji bardziej szczegółowo.  
  
## <a name="optimize-module-loading"></a>Optymalizacja ładowania modułu  
 Użyj narzędzi takich jak Eksplorator procesu (Procexp.exe) i Tlist.exe, aby określić, które moduły aplikacji ładuje. Polecenie `Tlist <pid>` pokazuje wszystkie moduły, które są ładowane przez proces.  
  
 Na przykład jeśli nie jest nawiązywane w sieci Web i Zobacz System.Web.dll jest załadowane, a następnie w aplikacji znajduje się moduł odwołujący się tego zestawu. Sprawdź, czy jest konieczne.  
  
 Jeśli aplikacja ma wiele modułów, scalić je jeden moduł. Ta metoda wymaga mniejsze koszty ładowania zestawu CLR. Mniejszą liczbę zestawów także oznaczać, że CLR zachowuje stan mniej.  
  
## <a name="defer-initialization-operations"></a>Odroczenie operacji inicjowania  
 Należy rozważyć opóźnienia kod inicjujący dopiero po wyrenderowaniu w głównym oknie aplikacji.  
  
 Należy pamiętać, można przeprowadzić inicjowania w konstruktorze klasy, czy kod inicjujący odwołuje się do innych klas, może spowodować efekt kaskadowych, w którym są wykonywane wiele konstruktorów klas.  
  
## <a name="avoid-application-configuration"></a>Unikaj konfiguracji aplikacji  
 Należy rozważyć unikanie konfiguracji aplikacji. Na przykład jeśli aplikacja ma prostą konfigurację wymagań i celów czasu uruchomienia strict, wpisy rejestru lub prostego pliku INI może być szybsze zamiast uruchamiania.  
  
## <a name="utilize-the-gac"></a>Korzystanie z pamięci podręcznej GAC  
 Jeśli zestaw nie jest zainstalowany w globalnej pamięci podręcznej zestawów (GAC), występują opóźnienia powodowane przez Weryfikacja skrótu zestawów o silnych nazwach i sprawdzania poprawności obrazów Ngen, jeśli obraz macierzysty dla tego zestawu jest dostępny na komputerze. Weryfikacja silnej nazwy zostało pominięte dla wszystkich zestawów zainstalowanych w pamięci GAC. Aby uzyskać więcej informacji, zobacz [Gacutil.exe (narzędzie globalnej pamięci podręcznej zestawów)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Użyj Ngen.exe  
 Należy rozważyć użycie Generator obrazu natywnego (Ngen.exe) w swojej aplikacji. Przy użyciu Ngen.exe oznacza handlowymi użycie procesora CPU, więcej dostępu do dysku, ponieważ może być większa niż obrazu MSIL obrazu macierzystego generowane przez Ngen.exe.  
  
 Aby skrócić czas ponowne uruchomienia, należy zawsze używać Ngen.exe w swojej aplikacji, ponieważ dzięki temu można uniknąć kosztów Procesora kompilacji JIT kodu aplikacji.  
  
 W niektórych scenariuszach zimnych uruchamiania przy użyciu Ngen.exe może być również przydatne. Jest to spowodowane kompilatora JIT (mscorjit.dll) musi być załadowany.  
  
 Zarówno Ngen i JIT moduły mogą mieć wpływ najgorszy. To dlatego mscorjit.dll muszą zostać załadowane, a podczas przy użyciu kompilatora JIT działa w kodzie, liczbę stron w obrazów Ngen muszą być dostępne, gdy przy użyciu kompilatora JIT odczytuje metadane te zestawy.  
  
### <a name="ngen-and-clickonce"></a>Narzędzie ngen i ClickOnce  
 Sposób planowania wdrażania aplikacji można również ustawić różnica w czasie ładowania. [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] wdrożenie aplikacji nie obsługuje narzędzia Ngen. Jeśli zdecydujesz się użyć Ngen.exe dla aplikacji, należy użyć innego mechanizmu wdrażania, takich jak Instalator Windows.  
  
 Aby uzyskać więcej informacji, zobacz [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Rebasing i rozwiązać problemy z biblioteki DLL  
 Jeśli używasz Ngen.exe, należy pamiętać, że zmienianie bazy może wystąpić, gdy załadowanych do pamięci obrazów macierzystych. Jeśli biblioteki DLL nie został załadowany preferowany adres podstawowy, ponieważ ten zakres adresów jest już przydzielony, moduł ładujący systemu Windows załaduje go na inny adres, który może być czasochłonna operacja.  
  
 Aby sprawdzić, czy są moduły, w których wszystkie strony są prywatne, można użyć narzędzia wirtualny adres zrzutu (Vadump.exe). Jeśli tak jest, moduł może został przebazowanych na inny adres. W związku z tym nie może być współużytkowana jego stron.  
  
 Aby uzyskać więcej informacji na temat ustawiania adres podstawowy, zobacz [Ngen.exe (Generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Optymalizacja kodu Authenticode  
 Weryfikacja Authenticode dodaje do czasu uruchomienia. Zestawy podpisane Authenticode trzeba można zweryfikować z urzędem certyfikacji (CA). Weryfikacji może być czasochłonne, ponieważ może wymagać, łączących się z siecią kilka razy, aby pobrać bieżącej listy odwołania certyfikatów. Również daje to pewność, że jest pełny łańcuch prawidłowe certyfikaty na ścieżce zaufany główny urząd certyfikacji. To może dokonywać translacji na kilka sekund opóźnienia podczas ładowania zestawu.  
  
 Zaleca się zainstalowanie certyfikatu urzędu certyfikacji na komputerze klienckim lub Unikaj używania Authenticode, gdy jest możliwe. Jeśli znasz aplikacja nie wymaga dowód wydawcy, nie masz zapłacenia koszt weryfikacji podpisu.  
  
 Począwszy od [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ma opcji konfiguracji, umożliwiający weryfikacji Authenticode obejście. Aby to zrobić, Dodaj następujące ustawienie do pliku app.exe.config:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Aby uzyskać więcej informacji, zobacz [ \<generatePublisherEvidence > elementu](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Porównanie wydajności w systemie Windows Vista  
 Menedżer pamięci w systemie Windows Vista ma mechanizmu wstępne ładowanie do pamięci. Wstępne ładowanie do pamięci analizuje wzorce użycia pamięci w czasie, aby określić zawartość optymalne pamięci dla określonego użytkownika. Działa on stale do obsługi tej zawartości przez cały czas.  
  
 Ta metoda różni się od pobierania wstępnego zastosowanych w systemie Windows XP, wstępnie ładuje dane w pamięci bez analizowania wzorców użycia. Wraz z upływem czasu Jeśli użytkownik używa aplikacji WPF często w systemie Windows Vista, czas uruchomienia zimnych aplikacji może poprawić.  
  
## <a name="use-appdomains-efficiently"></a>Efektywnie korzystać z domen aplikacji  
 Jeśli to możliwe ładowanie zestawów do obszaru kodu neutralne dla domen, aby upewnić się, że obrazu macierzystego, jeśli istnieje, jest używana w wszystkich domen aplikacji utworzony w aplikacji.  
  
 Aby uzyskać najlepszą wydajność należy wymusić sprawną komunikację między domenami zmniejszając wywołań między domenami. Jeśli to możliwe, należy użyć wywołania bez argumentów lub z argumentami typu pierwotnego.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Za pomocą atrybutu NeutralResourcesLanguage  
 Użyj <xref:System.Resources.NeutralResourcesLanguageAttribute> do określenia kultury neutralnej dla <xref:System.Resources.ResourceManager>. Takie podejście pozwala uniknąć wyszukiwań zestawu nie powiodło się.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Klasa elementu BinaryFormatter między elementami służy do serializacji  
 Jeśli musisz użyć serializacji, użyj <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy zamiast <xref:System.Xml.Serialization.XmlSerializer> klasy. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Klasy jest zaimplementowana w bibliotece klasy podstawowej (BCL) w zestawie mscorlib.dll. <xref:System.Xml.Serialization.XmlSerializer> Jest zaimplementowana w zestawie System.Xml.dll, która może być dodatkowe biblioteki DLL do załadowania.  
  
 Jeśli musisz użyć <xref:System.Xml.Serialization.XmlSerializer> klasy, ale można osiągnąć lepszą wydajność Jeśli wstępnie wygenerować zestawu serializacji.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Skonfiguruj ClickOnce do wyboru aktualizacji po uruchomieniu  
 Jeśli aplikacja używa [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], uniknąć przez skonfigurowanie dostępu do sieci podczas uruchamiania [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] do sprawdzenia lokacji wdrożenia aktualizacji po uruchomieniu aplikacji.  
  
 Jeśli używasz modelu aplikacji (XBAP) przeglądarki XAML, należy pamiętać, że [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] sprawdza lokacji wdrażania aktualizacji, nawet jeśli jest już XBAP [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [zabezpieczenia ClickOnce i wdrażania](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Automatycznie skonfigurować usługę PresentationFontCache do ekranu startowego  
 Usługa PresentationFontCache jest pierwszy do uruchomienia po ponownym uruchomieniu aplikacji WPF. Usługa buforuje czcionki systemowe, zwiększa dostępu czcionki i zwiększa ogólną wydajność. Brak obciążenie podczas uruchamiania usługi, a w niektórych środowiskach kontrolowanego, należy rozważyć skonfigurowanie usługi do automatycznego uruchamiania, po ponownym uruchomieniu systemu.  
  
## <a name="set-data-binding-programmatically"></a>Ustaw programowo powiązanie danych  
 Zamiast przy użyciu kodu XAML, aby ustawić <xref:System.Windows.FrameworkElement.DataContext%2A> deklaratywnie w oknie głównym, należy wziąć pod uwagę ustawieniem dla niego programowo w <xref:System.Windows.Application.OnActivated%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.SplashScreen>  
 <xref:System.AppDomain>  
 <xref:System.Resources.NeutralResourcesLanguageAttribute>  
 <xref:System.Resources.ResourceManager>  
 [Dodawanie ekranu powitalnego do aplikacji WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)  
 [Ngen.exe (generator obrazu natywnego)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [\<generatePublisherEvidence > — Element](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
