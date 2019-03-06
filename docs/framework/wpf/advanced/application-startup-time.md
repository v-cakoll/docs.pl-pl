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
ms.openlocfilehash: 0bd7875f1e819497ea3a4d846a2876084a54ab80
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379110"
---
# <a name="application-startup-time"></a>Czas uruchamiania aplikacji
Ilość czasu, która jest wymagana dla aplikacji WPF rozpocząć może się znacznie różnić. W tym temacie opisano różne techniki skracanie czasu uruchamiania postrzegany wartość rzeczywista dla aplikacji Windows Presentation Foundation (WPF).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Opis zimnego uruchamiania i uruchamiania bez wyłączania zasilania  
 Podczas zimnego uruchamiania występuje, gdy aplikacja uruchamia się po raz pierwszy po ponownym uruchomieniu systemu lub podczas uruchamiania aplikacji zamknij go, a następnie uruchom go ponownie po długim okresie czasu. Podczas uruchamiania aplikacji, jeśli wymagane stron (kod, dane statyczne, rejestru itp.) nie są obecne na liście wstrzymania Windows Menedżer pamięci, występują błędy stron. Dostęp do dysku jest wymagana do wprowadzenia strony w pamięci.  
  
 Bez wyłączania zasilania uruchamiania występuje, gdy większość na stronach głównych składników środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego zostały już załadowane w pamięci, co pozwala zaoszczędzić czas dostępu drogich dysków. Właśnie dlatego aplikacji zarządzanej rozpoczyna się szybciej, gdy jest uruchamiany po raz drugi.  
  
## <a name="implement-a-splash-screen"></a>Implementowanie ekran powitalny  
 W przypadkach, gdy jest istotne, nieuniknione opóźnienie między uruchomieniem aplikacji oraz wyświetlanie pierwszego interfejsu użytkownika, optymalizowanie czasu uruchamiania postrzegany przy użyciu *ekran powitalny*. Ta metoda Wyświetla obraz niemal natychmiast po użytkownik uruchamia aplikację. Gdy aplikacja jest gotowa do wyświetlenia jego pierwszego interfejsu użytkownika, stopniowo zmienia się na ekranie powitalnym. Począwszy od [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], możesz użyć <xref:System.Windows.SplashScreen> klasy do zaimplementowania ekran powitalny. Aby uzyskać więcej informacji, zobacz [dodać ekran powitalny do aplikacji WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Możesz również wdrożyć ekranu powitalnego za pomocą natywnego grafiki Win32. Wyświetlanie implementacji przed <xref:System.Windows.Application.Run%2A> metoda jest wywoływana.  
  
## <a name="analyze-the-startup-code"></a>Analizowanie kodu startowego  
 Ustal przyczynę powolne zimnego uruchamiania. We/Wy dysku mogą być odpowiedzialne, ale nie zawsze jest to wymagane. Ogólnie rzecz biorąc należy zminimalizować użycie zasobów zewnętrznych, takich jak sieci, usługi sieci Web lub na dysku.  
  
 Przed testowaniem, sprawdź, czy nie inne uruchomione aplikacje lub usługi używają kodu zarządzanego lub kodu WPF.  
  
 Uruchomić aplikację WPF, natychmiast po ponownym uruchomieniu i określ, jak długo trwa do wyświetlenia. W przypadku znacznie szybciej wszystkich kolejnych uruchomień aplikacji (uruchomienia bez wyłączania zasilania) problem podczas zimnego uruchamiania najprawdopodobniej spowodowane przez operacje We/Wy.  
  
 Jeśli aplikacja zimnego uruchamiania nie dotyczy problem operacji We/Wy, jest prawdopodobne, że Twoja aplikacja działa niektóre długich inicjowania lub obliczenie i czeka na niektóre zdarzenia ukończyć, lub wymaga dużo kompilacja JIT przy uruchamianiu. W następujących sekcjach opisano niektóre z tych sytuacji bardziej szczegółowo.  
  
## <a name="optimize-module-loading"></a>Optymalizowanie ładowania modułu  
 Użyj narzędzi takich jak Eksplorator procesów (Procexp.exe) i Tlist.exe, aby określić, które moduły aplikacja ładuje. Polecenie `Tlist <pid>` Wyświetla wszystkie moduły, które są ładowane przez proces.  
  
 Na przykład jeśli nie jest nawiązywane w sieci Web jest ładowany System.Web.dll, a następnie w aplikacji jest moduł, odwołuje się do tego zestawu. Sprawdź, czy jest to konieczne.  
  
 Jeśli aplikacja ma wiele modułów, scalić w pojedynczym module. Takie podejście wymaga mniejsze koszty ładowania zestawu CLR. Mniejszej liczby zestawów także oznaczać, że środowisko CLR utrzymuje mniej stanu.  
  
## <a name="defer-initialization-operations"></a>Odroczenie inicjowania operacji  
 Należy wziąć pod uwagę odracza kod inicjujący aż po wyrenderowaniu okna głównego aplikacji.  
  
 Należy pamiętać, że może być wykonana inicjalizacji w konstruktorze klasy, a kod inicjujący odwołuje się do innych klas, może spowodować efektu kaskadowego, w którym są wykonywane wiele konstruktorów klas.  
  
## <a name="avoid-application-configuration"></a>Należy unikać konfiguracji aplikacji  
 Należy wziąć pod uwagę, unikając konfiguracji aplikacji. Na przykład jeśli aplikacja ma prostej konfiguracji wymagań i celów czasu uruchamiania ściśle, wpisy rejestru lub prostego pliku INI może być szybsze zamiast uruchamiania.  
  
## <a name="utilize-the-gac"></a>Korzystanie z pamięci podręcznej GAC  
 Zestaw nie jest zainstalowany w globalnej pamięci podręcznej zestawów (GAC), czy opóźnienia spowodowane tym, że weryfikacja skrótu zestawów o silnych nazwach i sprawdzania poprawności obrazów Ngen obraz natywny dla tego zestawu znajduje się na komputerze. Weryfikacja silnej nazwy jest pomijana dla wszystkich zestawów zainstalowane w GAC. Aby uzyskać więcej informacji, zobacz [Gacutil.exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Użyj Ngen.exe  
 Należy rozważyć użycie Native Image Generator (Ngen.exe) w swojej aplikacji. Użycie Ngen.exe oznacza, handlem użycia procesora CPU, więcej dostępu do dysku, ponieważ może być większe od obrazu MSIL obrazu natywnego wygenerowanego przez Ngen.exe.  
  
 Aby poprawić czas uruchamiania bez wyłączania zasilania, należy zawsze używać Ngen.exe w swojej aplikacji, ponieważ pozwala to uniknąć użycia Procesora CPU kompilacji JIT kodu aplikacji.  
  
 W niektórych scenariuszach podczas zimnego uruchamiania przy użyciu Ngen.exe może być również przydatne. Jest to spowodowane kompilator JIT (mscorjit.dll) nie będzie musiał zostać załadowany.  
  
 Moduły Ngen i JIT może mieć wpływ najgorszy. Jest to spowodowane mscorjit.dll muszą zostać załadowane, a gdy kompilator JIT pracuje nad kodem, liczbę stron w obrazów Ngen muszą być dostępne, gdy kompilator JIT czyta metadane zestawów.  
  
### <a name="ngen-and-clickonce"></a>Ngen i technologii ClickOnce  
 Sposób, którą chcesz wdrożyć aplikację można również ustawić różnica w czasie ładowania. [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] wdrożenie aplikacji nie obsługuje polecenia Ngen. Jeśli zdecydujesz się użyć Ngen.exe dla aplikacji, należy użyć innego mechanizmu wdrażania, takich jak Instalator Windows.  
  
 Aby uzyskać więcej informacji, zobacz [Ngen.exe (Generator obrazu natywnego)](../../tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Rebasing i konflikty adresów biblioteki DLL  
 Użycie Ngen.exe, należy pamiętać, że zmienianie bazy może wystąpić, gdy obrazy natywne są ładowane do pamięci. Jeśli biblioteka DLL nie jest ładowany w swoim preferowanym adresem bazowym, ponieważ ten zakres adresów jest już przydzielony, moduł ładujący Windows załaduje go na inny adres, który może być czasochłonna operacja.  
  
 Aby sprawdzić, czy istnieją moduły, w których wszystkie strony są prywatne, można użyć narzędzia wirtualnego adresu zrzutu (Vadump.exe). Jeśli jest to możliwe, moduł może została zmieniona na inny adres. W związku z tym nie można współużytkować jego stron.  
  
 Aby uzyskać więcej informacji o tym, jak ustawić adres podstawowy, zobacz [Ngen.exe (Generator obrazu natywnego)](../../tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Optymalizowanie Authenticode  
 Weryfikacja Authenticode dodaje do czasu uruchamiania. Zestawy z podpisem Authenticode trzeba można sprawdzić przy użyciu urzędu certyfikacji (CA). Ta weryfikacja może być czasochłonne, ponieważ może wymagać, nawiązywanie połączenia z siecią kilka razy pobieranie bieżącej listy odwołania certyfikatów. Zapewnia się także pewność, że pełny łańcuch prawidłowe certyfikaty na ścieżce zaufany główny urząd certyfikacji. To może dokonywać translacji na kilka sekund opóźnienia podczas ładowania zestawu.  
  
 Należy rozważyć zainstalowanie certyfikatu urzędu certyfikacji na komputerze klienckim lub Unikaj używania Authenticode, gdy jest to możliwe. Jeśli wiesz, aplikacja nie wymaga dowód wydawcy, nie trzeba naliczana jest opłata za weryfikacji podpisu.  
  
 Począwszy od [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ma opcji konfiguracji, która umożliwia weryfikacji Authenticode do obejścia. Aby to zrobić, Dodaj następujące ustawienie do pliku app.exe.config:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Aby uzyskać więcej informacji, zobacz [ \<generatePublisherEvidence > Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Porównanie wydajności w systemie Windows Vista  
 Menedżer pamięci w Windows Vista ma technologia o nazwie wstępne ładowanie do pamięci. Wstępne ładowanie do pamięci analizuje wzorce użycia pamięci wraz z upływem czasu, aby określić zawartość pamięci optymalne dla określonego użytkownika. Działa ona nieprzerwanie do obsługi tej zawartości przez cały czas.  
  
 To podejście różni się od pobierania wstępnego zastosowanych w Windows XP wstępnie ładuje dane do pamięci bez analizowanie wzorców użycia. Wraz z upływem czasu Jeśli użytkownik używa aplikacji środowiska WPF często w Windows Vista, zwiększyć czas podczas zimnego uruchamiania aplikacji.  
  
## <a name="use-appdomains-efficiently"></a>Efektywnie wykorzystać domen aplikacji  
 Jeśli to możliwe ładowanie zestawów do obszaru kodu neutralnego względem domeny, aby upewnić się, że obrazu natywnego, jeśli istnieje, jest stosowana w wszystkich domen aplikacji utworzonych w aplikacji.  
  
 Aby uzyskać najlepszą wydajność wymusić sprawną komunikację między domenami, zmniejszając wywołania między domenami. Jeśli to możliwe, należy użyć wywołania bez argumentów lub z argumentami typu pierwotnego.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Użyj atrybutu NeutralResourcesLanguage  
 Użyj <xref:System.Resources.NeutralResourcesLanguageAttribute> do określenia kultury neutralnej dla <xref:System.Resources.ResourceManager>. W tym podejściu unika zestawu niepomyślnych wyszukiwań.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Korzystanie z klasy elementu do serializacji  
 Jeśli musisz użyć serializacji, należy użyć <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy zamiast <xref:System.Xml.Serialization.XmlSerializer> klasy. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Klasy jest zaimplementowana w Biblioteka klasy podstawowej (BCL) w zestawie biblioteki mscorlib.dll. <xref:System.Xml.Serialization.XmlSerializer> Jest zaimplementowana w zestawie System.Xml.dll, która może być dodatkowe biblioteki DLL do załadowania.  
  
 Jeśli musisz użyć <xref:System.Xml.Serialization.XmlSerializer> klasy, można osiągnąć lepszą wydajność w przypadku wstępnie wygenerować zestawu serializacji.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Konfigurowanie ClickOnce, aby sprawdzić aktualizacje po uruchomieniu  
 Jeśli aplikacja używa [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], unikaj dostępu do sieci podczas uruchamiania, konfigurując [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] do sprawdzenia lokacji wdrożenia aktualizacji po uruchomieniu aplikacji.  
  
 Jeśli używasz modelu (XBAP) aplikacji przeglądarki XAML, należy pamiętać, że [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] sprawdza lokacji wdrożenia aktualizacji, nawet jeśli jest już XBAP [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Automatycznie skonfigurować usługę PresentationFontCache do ekranu startowego  
 Do uruchomienia po ponownym uruchomieniu pierwszej aplikacji WPF to usługa PresentationFontCache. Usługa przechowuje czcionki systemowe, zwiększa czcionki dostęp i zwiększa ogólną wydajność. Występuje obciążenie podczas uruchamiania usługi, a w niektórych środowiskach kontrolowanego, rozważ skonfigurowanie usługi do automatycznego uruchamiania, po ponownym rozruchu systemu.  
  
## <a name="set-data-binding-programmatically"></a>Ustaw programowo powiązania danych  
 Zamiast przy użyciu XAML, aby ustawić <xref:System.Windows.FrameworkElement.DataContext%2A> deklaratywnie w głównym oknie, warto ustawić programowo w <xref:System.Windows.Application.OnActivated%2A> metody.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [Dodawanie ekranu powitalnego do aplikacji WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (generator obrazu natywnego)](../../tools/ngen-exe-native-image-generator.md)
- [\<generatePublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
