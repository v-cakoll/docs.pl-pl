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
ms.openlocfilehash: 0fae3ac1769163101dcdb183f4c5c2135354b1fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145426"
---
# <a name="application-startup-time"></a>Czas uruchamiania aplikacji
Ilość czasu, który jest wymagany dla aplikacji WPF do uruchomienia może się znacznie różnić. W tym temacie opisano różne techniki skracania czasu uruchamiania postrzegane i rzeczywiste dla aplikacji Windows Presentation Foundation (WPF).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Zrozumienie zimnego uruchamiania i ciepłego uruchamiania  
 Zimne uruchamianie występuje, gdy aplikacja uruchamia się po raz pierwszy po ponownym uruchomieniu systemu lub po uruchomieniu aplikacji, zamknij ją, a następnie uruchom ponownie po długim czasie. Po uruchomieniu aplikacji, jeśli wymagane strony (kod, dane statyczne, rejestr itp.) nie są obecne na liście rezerwowej menedżera pamięci systemu Windows, występują błędy strony. Dostęp do dysku jest wymagany do wprowadzenia stron do pamięci.  
  
 Ciepłe uruchamianie występuje, gdy większość stron dla składników głównego środowiska wykonawczego języka wspólnego (CLR) jest już załadowana do pamięci, co oszczędza kosztowny czas dostępu do dysku. Dlatego aplikacja zarządzana uruchamia się szybciej, gdy działa po raz drugi.  
  
## <a name="implement-a-splash-screen"></a>Implementowanie ekranu powitalnego  
 W przypadkach, gdy występuje znaczne, nieuniknione opóźnienie między uruchomieniem aplikacji a wyświetlaniem pierwszego interfejsu użytkownika, zoptymalizuj czas uruchamiania za pomocą *ekranu powitalnego.* Takie podejście wyświetla obraz niemal natychmiast po uruchomieniu aplikacji przez użytkownika. Gdy aplikacja jest gotowa do wyświetlenia pierwszego interfejsu użytkownika, ekran powitalny zanika. Począwszy od .NET Framework 3.5 SP1, można użyć <xref:System.Windows.SplashScreen> klasy do zaimplementowania ekranu powitalnego. Aby uzyskać więcej informacji, zobacz [Dodawanie ekranu powitalnego do aplikacji WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Można również zaimplementować własny ekran powitalny przy użyciu natywnej grafiki Win32. Wyświetl implementację <xref:System.Windows.Application.Run%2A> przed wywołaniem metody.  
  
## <a name="analyze-the-startup-code"></a>Analizowanie kodu startowego  
 Określ przyczynę powolnego uruchamiania przeziębienia. We/Wy dysku mogą być odpowiedzialne, ale nie zawsze tak jest. Ogólnie rzecz biorąc należy zminimalizować użycie zasobów zewnętrznych, takich jak sieć, usługi sieci Web lub dysk.  
  
 Przed przetestowaniem sprawdź, czy żadne inne uruchomione aplikacje lub usługi nie używają kodu zarządzanego lub kodu WPF.  
  
 Uruchom aplikację WPF natychmiast po ponownym uruchomieniu komputera i określ, jak długo trwa wyświetlanie. Jeśli wszystkie kolejne uruchomienia aplikacji (ciepłe uruchamianie) są znacznie szybsze, problem zimnego uruchamiania jest najprawdopodobniej spowodowany przez we/wy.  
  
 Jeśli problem zimnego uruchamiania aplikacji nie jest związany z we/wy, jest prawdopodobne, że aplikacja wykonuje pewne długie inicjowanie lub obliczenia, czeka na zakończenie jakiegoś zdarzenia lub wymaga dużo kompilacji JIT podczas uruchamiania. W poniższych sekcjach opisano niektóre z tych sytuacji bardziej szczegółowo.  
  
## <a name="optimize-module-loading"></a>Optymalizacja ładowania modułu  
 Użyj narzędzi, takich jak Process Explorer (Procexp.exe) i Tlist.exe, aby określić, które moduły ładuje aplikacja. Polecenie `Tlist <pid>` pokazuje wszystkie moduły, które są ładowane przez proces.  
  
 Na przykład jeśli nie łączysz się z siecią Web i widzisz, że System.Web.dll jest ładowany, a następnie istnieje moduł w aplikacji, który odwołuje się do tego zestawu. Sprawdź, czy odwołanie jest konieczne.  
  
 Jeśli aplikacja ma wiele modułów, scal je w jeden moduł. Takie podejście wymaga mniej clr obciążenia zestawu obciążenie. Mniej zestawów oznacza również, że CLR utrzymuje mniej stanu.  
  
## <a name="defer-initialization-operations"></a>Odraczaj operacje inicjowania  
 Należy rozważyć odroczenie kodu inicjowania, dopóki po renderowaniu głównego okna aplikacji.  
  
 Należy pamiętać, że inicjowanie może być wykonywane wewnątrz konstruktora klasy, a jeśli kod inicjowania odwołuje się do innych klas, może to spowodować efekt kaskadowy, w którym wykonuje się wiele konstruktorów klas.  
  
## <a name="avoid-application-configuration"></a>Unikaj konfiguracji aplikacji  
 Należy rozważyć unikanie konfiguracji aplikacji. Na przykład, jeśli aplikacja ma proste wymagania konfiguracyjne i ma ścisłe cele czasu uruchamiania, wpisy rejestru lub prosty plik INI może być szybszą alternatywą uruchamiania.  
  
## <a name="utilize-the-gac"></a>Wykorzystaj GAC  
 Jeśli zestaw nie jest zainstalowany w globalnej pamięci podręcznej zestawów (GAC), istnieją opóźnienia spowodowane weryfikacją mieszania zestawów o silnych nazwach i sprawdzaniem poprawności obrazu Ngen, jeśli na komputerze jest dostępny obraz macierzysty dla tego zestawu. Weryfikacja silnej nazwy jest pomijana dla wszystkich zestawów zainstalowanych w pliku GAC. Aby uzyskać więcej informacji, zobacz [Gacutil.exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md) (Program Gacutil.exe — narzędzie do obsługi globalnej pamięci podręcznej zestawów).  
  
## <a name="use-ngenexe"></a>Użyj Ngen.exe  
 Należy rozważyć użycie generatora obrazów natywnych (Ngen.exe) w aplikacji. Korzystanie z Ngen.exe oznacza handel zużyciem procesora cpu dla większego dostępu do dysku, ponieważ natywny obraz generowany przez Ngen.exe może być większy niż obraz MSIL.  
  
 Aby poprawić ciepły czas uruchamiania, należy zawsze używać Ngen.exe w aplikacji, ponieważ pozwala to uniknąć kosztu procesora kompilacji JIT kodu aplikacji.  
  
 W niektórych scenariuszach zimnego uruchamiania pomocne może być również użycie pliku Ngen.exe. Dzieje się tak, ponieważ kompilator JIT (mscorjit.dll) nie musi być ładowany.  
  
 Posiadanie modułów Ngen i JIT może mieć najgorszy efekt. Jest to spowodowane mscorjit.dll musi być załadowany, a gdy kompilator JIT działa na kod, wiele stron w obrazach Ngen musi być dostępny, gdy kompilator JIT odczytuje metadane zestawów.  
  
### <a name="ngen-and-clickonce"></a>Ngen i ClickOnce  
 Sposób planowania wdrażania aplikacji może również mieć wpływ na czas ładowania. ClickOnce wdrożenie aplikacji nie obsługuje Ngen. Jeśli zdecydujesz się użyć programu Ngen.exe dla aplikacji, należy użyć innego mechanizmu wdrażania, takiego jak Instalator Windows.  
  
 Aby uzyskać więcej informacji, zobacz [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Ponowne uszowanie bazy i kolizje adresów DLL  
 Jeśli używasz programu Ngen.exe, należy pamiętać, że ponowne tworzenie bazy może wystąpić, gdy obrazy natywne są ładowane do pamięci. Jeśli biblioteka DLL nie jest ładowana pod preferowanym adresem podstawowym, ponieważ ten zakres adresów jest już przydzielony, program ładujący systemu Windows załaduje go pod innym adresem, co może być czasochłonną operacją.  
  
 Za pomocą narzędzia Vadump.exe) można użyć narzędzia Vadump.exe, aby sprawdzić, czy istnieją moduły, w których wszystkie strony są prywatne. W takim przypadku moduł mógł zostać ponownie oparty na innym adresie. W związku z tym jego strony nie mogą być udostępniane.  
  
 Aby uzyskać więcej informacji na temat ustawiania adresu bazowego, zobacz [Ngen.exe (Generator obrazu natywnego).](../../tools/ngen-exe-native-image-generator.md)  
  
## <a name="optimize-authenticode"></a>Optymalizacja autentycznegoode  
 Weryfikacja authenticode dodaje czas uruchamiania. Zestawy podpisane z uwierzytelnie muszą zostać zweryfikowane za pomocą urzędu certyfikacji(CA). Ta weryfikacja może być czasochłonna, ponieważ może wymagać kilkukrotnego połączenia z siecią w celu pobrania bieżących list odwołania certyfikatów. Zapewnia również, że istnieje pełny łańcuch prawidłowych certyfikatów na ścieżce do zaufanego katalogu głównego. Może to przełożyć się na kilka sekund opóźnienia podczas ładowania zestawu.  
  
 Należy rozważyć zainstalowanie certyfikatu urzędu certyfikacji na komputerze klienckim lub unikać używania authenticode, gdy jest to możliwe. Jeśli wiesz, że aplikacja nie potrzebuje dowodów wydawcy, nie musisz płacić kosztów weryfikacji podpisu.  
  
 Począwszy od programu .NET Framework 3.5, istnieje opcja konfiguracji, która umożliwia weryfikację Authenticode, aby pominąć. Aby to zrobić, dodaj następujące ustawienie do pliku app.exe.config:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>
    </runtime>  
</configuration>  
```  
  
 Aby uzyskać więcej informacji, zobacz [ \<generatePublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Porównanie wydajności w systemie Windows Vista  
 Menedżer pamięci w systemie Windows Vista ma technologię o nazwie SuperFetch. SuperFetch analizuje wzorce użycia pamięci w czasie, aby określić optymalną zawartość pamięci dla określonego użytkownika. Działa w sposób ciągły, aby utrzymać tę zawartość przez cały czas.  
  
 Takie podejście różni się od techniki pobierania wstępnego używanej w systemie Windows XP, która wstępnie ładuje dane do pamięci bez analizowania wzorców użycia. Z biegiem czasu, jeśli użytkownik często używa aplikacji WPF w systemie Windows Vista, czas zimnego uruchamiania aplikacji może ulec poprawie.  
  
## <a name="use-appdomains-efficiently"></a>Efektywne korzystanie z aplikacji AppDomains  
 Jeśli to możliwe, należy załadować zestawy do obszaru kodu neutralnego dla domeny, aby upewnić się, że obraz macierzysty, jeśli istnieje, jest używany we wszystkich AppDomains utworzonych w aplikacji.  
  
 Aby uzyskać najlepszą wydajność, wymusz wydajną komunikację między domenami, zmniejszając liczbę połączeń między domenami. Jeśli to możliwe, należy używać wywołań bez argumentów lub z argumentami typu pierwotnego.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Użyj atrybutu NeutralResourcesLanguage  
 Użyj, <xref:System.Resources.NeutralResourcesLanguageAttribute> aby określić kultury <xref:System.Resources.ResourceManager>neutralnej dla . Takie podejście pozwala uniknąć nieudanych odnośów zestawu.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Użyj klasy BinaryFormatter do serializacji  
 Jeśli należy użyć serializacji, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> należy użyć <xref:System.Xml.Serialization.XmlSerializer> klasy zamiast klasy. Klasa <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> jest implementowana w bibliotece klas podstawowych (BCL) w zestawie mscorlib.dll. Jest <xref:System.Xml.Serialization.XmlSerializer> zaimplementowana w zestawie System.Xml.dll, który może być dodatkową biblioteką DLL do załadowania.  
  
 Jeśli należy użyć <xref:System.Xml.Serialization.XmlSerializer> klasy, można osiągnąć lepszą wydajność, jeśli wstępnie wygenerować zestaw serializacji.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Konfigurowanie ClickOnce do sprawdzania dostępności aktualizacji po uruchomieniu  
 Jeśli aplikacja używa ClickOnce, należy unikać dostępu do sieci podczas uruchamiania, konfigurując ClickOnce, aby sprawdzić witrynę wdrażania pod kątem aktualizacji po uruchomieniu aplikacji.  
  
 Jeśli używasz modelu aplikacji przeglądarki XAML (XBAP), należy pamiętać, że ClickOnce sprawdza witrynę wdrażania pod kątem aktualizacji, nawet jeśli XBAP jest już w pamięci podręcznej ClickOnce. Aby uzyskać więcej informacji, zobacz [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Konfigurowanie usługi PresentationFontCache do automatycznego uruchamiania  
 Pierwszą aplikacją WPF do uruchomienia po ponownym uruchomieniu jest PresentationFontCache usługi. Usługa buforuje czcionki systemowe, poprawia dostęp do czcionek i zwiększa ogólną wydajność. Istnieje obciążenie podczas uruchamiania usługi, a w niektórych kontrolowanych środowiskach należy rozważyć skonfigurowanie usługi do automatycznego uruchamiania po ponownym uruchomieniu systemu.  
  
## <a name="set-data-binding-programmatically"></a>Programowo ustawianie powiązania danych  
 Zamiast używać XAML, aby <xref:System.Windows.FrameworkElement.DataContext%2A> ustawić deklaratywnie dla okna głównego, <xref:System.Windows.Application.OnActivated%2A> należy rozważyć ustawienie go programowo w metodzie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [Dodaj ekran powitalny do aplikacji WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (Generator obrazu natywnego)](../../tools/ngen-exe-native-image-generator.md)
- [\<generatePublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
