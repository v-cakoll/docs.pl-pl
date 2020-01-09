---
title: Strategia zabezpieczeń WPF - zabezpieczenia platformy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
ms.openlocfilehash: b2fd923de165c0926e6f812764c71127b7c27691
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636240"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategia zabezpieczeń WPF - zabezpieczenia platformy
Chociaż Windows Presentation Foundation (WPF) oferuje różne usługi zabezpieczeń, wykorzystuje również funkcje zabezpieczeń podstawowej platformy, w tym system operacyjny, środowisko CLR i program Internet Explorer. Te warstwy są łączone w celu zapewnienia mocnego, kompleksowego modelu zabezpieczeń, który podejmuje próbę uniknięcia wszelkich single point of failure, jak pokazano na poniższej ilustracji:  
  
 ![Diagram przedstawiający model zabezpieczeń WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 W pozostałej części tego tematu omówiono funkcje w każdej z tych warstw, które odnoszą się do platformy WPF.  

## <a name="operating-system-security"></a>Zabezpieczenia systemu operacyjnego  
Rdzeń systemu Windows zawiera kilka funkcji zabezpieczeń, które tworzą podstawę zabezpieczeń dla wszystkich aplikacji systemu Windows, w tym tych utworzonych za pomocą WPF. W tym temacie omówiono zakres tych funkcji zabezpieczeń, które są ważne dla platformy WPF, a także sposób, w jaki WPF integrują się z nimi w celu zapewnienia dalszej ochrony szczegółowej.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Oprócz ogólnego przeglądu i wzmocnienia systemu Windows, istnieją trzy kluczowe [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] funkcje, które można omawiać w tym temacie:  
  
- Kompilacja/GS  
  
- Microsoft Windows Update.  
  
#### <a name="gs-compilation"></a>Kompilacja/GS  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] zapewnia ochronę przez ponowną kompilację wielu podstawowych bibliotek systemowych, w tym wszystkich zależności WPF, takich jak środowisko CLR, aby pomóc w ograniczeniu przekroczenia buforu. Jest to osiągane przy użyciu parametru/GS z kompilatorem wierszaC++ polecenia C/. Mimo że przepełnienia buforów należy jawnie uniknąć, kompilacja/GS oferuje przykład obrony przed potencjalnymi lukami, które są przypadkowo lub złośliwie tworzone przez nie.  
  
 W przeszłości przekroczenia buforu były przyczyną wielu luk w zabezpieczeniach o dużym wpływie. Przepełnienie buforu występuje, gdy osoba atakująca korzysta z luki w zabezpieczeniach kodu, która pozwala na wstrzyknięcie złośliwego kodu, który zapisuje się poza granicami buforu. Dzięki temu osoba atakująca może przejąć proces, w którym wykonywany jest kod, zastępując adres zwrotny funkcji, aby spowodować wykonanie kodu osoby atakującej. Wynikiem jest złośliwy kod, który wykonuje dowolny kod z takimi samymi uprawnieniami co proces przejęty.  
  
 Na wysokim poziomie flaga kompilatora-GS chroni przed niektórymi potencjalnymi przedziałami buforu poprzez wstrzyknięcie specjalnego pliku cookie zabezpieczeń w celu ochrony adresu zwrotnego funkcji, która ma lokalne bufory ciągów. Po powrocie funkcji plik cookie zabezpieczeń jest porównywany z poprzednią wartością. Jeśli wartość została zmieniona, może wystąpić przepełnienie buforu i proces zostanie zatrzymany z warunkiem błędu. Zatrzymanie procesu uniemożliwia wykonanie potencjalnie złośliwego kodu. Zobacz [-GS (sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) , aby uzyskać więcej szczegółów.  
  
 Funkcja WPF została skompilowana za pomocą flagi/GS w celu dodania innej warstwy obrony do aplikacji WPF.  
  
### <a name="windows-vista"></a>Windows Vista  
Użytkownicy WPF w systemie Windows Vista będą korzystać z dodatkowych ulepszeń zabezpieczeń systemu operacyjnego, takich jak "dostęp użytkownika z najwyższymi uprawnieniami", sprawdzanie integralności kodu i izolacja uprawnień.  
  
#### <a name="user-account-control-uac"></a>Kontrola konta użytkownika  
 Obecnie użytkownicy systemu Windows mogą uruchamiać się z uprawnieniami administratora, ponieważ wiele aplikacji wymaga ich do instalacji lub wykonania albo obu tych metod. Przykładem może być zapisanie domyślnych ustawień aplikacji do rejestru.  
  
 Uruchamianie z uprawnieniami administratora naprawdę oznacza, że aplikacje są wykonywane z procesów, które mają uprawnienia administratora. Wpływem bezpieczeństwa tego jest to, że dowolny złośliwy kod, który przejmuje proces z uprawnieniami administratora, będzie automatycznie dziedziczyć te uprawnienia, w tym dostęp do krytycznych zasobów systemu.  
  
 Jednym ze sposobów ochrony przed tym zagrożeniem bezpieczeństwa jest uruchomienie aplikacji z najmniejszą ilością wymaganych uprawnień. Jest to nazywane zasadą najniższych uprawnień i jest podstawową funkcją systemu operacyjnego Windows. Ta funkcja jest nazywana kontrolą konta użytkownika (UAC) i jest używana przez funkcję UAC systemu Windows na dwa sposoby:  
  
- Aby domyślnie uruchamiać większość aplikacji z uprawnieniami funkcji Kontrola konta użytkownika, nawet jeśli użytkownik jest administratorem. tylko aplikacje, które wymagają uprawnień administratora, będą uruchamiane z uprawnieniami administratora. Aby można było uruchamiać z uprawnieniami administracyjnymi, aplikacje muszą być jawnie oznaczone w manifeście aplikacji lub jako wpis w zasadach zabezpieczeń.  
  
- Zapewnianie rozwiązań zgodności, takich jak wirtualizacja. Przykładowo wiele aplikacji próbuje zapisywać w lokalizacjach z ograniczeniami, takimi jak C:\Program Files. W przypadku aplikacji uruchamianych w ramach funkcji Kontrola konta użytkownika istnieje alternatywna lokalizacja dla poszczególnych użytkowników, która nie wymaga uprawnień administratora do zapisu w usłudze. W przypadku aplikacji uruchamianych w ramach funkcji UAC funkcja Kontrola konta użytkownika umożliwia wirtualizację C:\Program Files w taki sposób, że aplikacje, które zauważają, że zapisu są w rzeczywistości zapisywane do alternatywnej lokalizacji na użytkownika. Ten rodzaj pracy zgodności umożliwia systemowi operacyjnemu uruchamianie wielu aplikacji, które nie mogły wcześniej działać w funkcji Kontrola konta użytkownika.  
  
#### <a name="code-integrity-checks"></a>Sprawdzanie integralności kodu  
 System Windows Vista zawiera dokładniejsze testy integralności kodu, które ułatwiają wprowadzanie złośliwego kodu do plików systemowych lub jądra w czasie ładowania/uruchamiania. Powoduje to przekroczenie ochrony plików systemowych.  
   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Ograniczony proces uprawnień dla aplikacji hostowanych w przeglądarce  
 Aplikacje WPF hostowane w przeglądarce są wykonywane w piaskownicy strefy internetowej. Integracja WPF z programem Microsoft Internet Explorer rozszerza tę ochronę dzięki dodatkowej obsłudze.  
  
 Ponieważ aplikacje przeglądarki XAML (XBAP) są zwykle piaskownicy przez zestaw uprawnień strefy internetowej, Usunięcie tych uprawnień nie jest szkodliwe dla aplikacji przeglądarki XAML (XBAP) z perspektywy zgodności. Zamiast tego zostanie utworzona dodatkowa warstwa zabezpieczeń. Jeśli aplikacja w trybie piaskownicy może wykorzystywać inne warstwy i przejmowanie tego procesu, proces nadal będzie miał tylko ograniczone uprawnienia.  
  
 Zobacz [Używanie konta użytkownika z najniższymi uprawnieniami](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
## <a name="common-language-runtime-security"></a>Zabezpieczenia środowiska uruchomieniowego języka wspólnego  
 Środowisko uruchomieniowe języka wspólnego (CLR) oferuje szereg najważniejszych korzyści z zabezpieczeń, które obejmują sprawdzanie poprawności i weryfikację, zabezpieczenia dostępu kodu (CAS) oraz krytyczną metodologię zabezpieczeń.  
    
### <a name="validation-and-verification"></a>Weryfikacja i weryfikacja  
 Aby zapewnić izolację i integralność zestawu, środowisko CLR używa procesu weryfikacji. Sprawdzanie poprawności środowiska CLR zapewnia odizolowanie zestawów przez zweryfikowanie ich przenośnego formatu pliku wykonywalnego (PE) dla adresów, które wskazują poza zestawem. Sprawdzanie poprawności środowiska CLR sprawdza również integralność metadanych osadzonych w zestawie.  
  
 Aby zapewnić bezpieczeństwo typów, należy zapobiec typowym problemom z zabezpieczeniami (na przykład przekroczenia buforu) i włączyć obsługę piaskownicy przez izolację podprocesów, a zabezpieczenia CLR wykorzystują koncepcję weryfikacji.  
  
 Aplikacje zarządzane są kompilowane do języka pośredniego firmy Microsoft (MSIL). Gdy są wykonywane metody w aplikacji zarządzanej, jej MSIL jest kompilowany do kodu natywnego za pomocą kompilacji just-in-Time (JIT). Kompilacja JIT obejmuje proces weryfikacji, który stosuje wiele reguł bezpieczeństwa i niezawodności, które gwarantują, że kod nie:  
  
- Narusza kontrakty typu  
  
- Wprowadź przekroczenia buforu  
  
- Bezznaczne dostęp do pamięci.  
  
 Nie można wykonać kodu zarządzanego, który jest niezgodny z regułami weryfikacji, chyba że jest uznawany za zaufany kod.  
  
 Zalety kodu możliwego do zweryfikowania to kluczowy powód, dla którego WPF kompiluje się na .NET Framework. W zakresie, w jakim jest używany kod możliwy do zweryfikowania, możliwość wykorzystania możliwych luk w zabezpieczeniach jest znacznie niższa.  
  
### <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 Komputer kliencki uwidacznia szeroką gamę zasobów, do których może mieć dostęp aplikacja zarządzana, w tym system plików, rejestr, usługi drukowania, interfejs użytkownika, odbicie i zmienne środowiskowe. Aby aplikacja zarządzana mogła uzyskać dostęp do dowolnych zasobów na komputerze klienckim, musi mieć odpowiednie uprawnienia .NET Framework. Uprawnienie w urzędach certyfikacji jest podklasą <xref:System.Security.CodeAccessPermission>; Urzędy certyfikacji implementują jedną podklasę dla każdego zasobu, do którego mogą uzyskać dostęp aplikacje zarządzane.  
  
 Zestaw uprawnień, które są przydzielane przez urzędy certyfikacji podczas uruchamiania, jest znany jako zestaw uprawnień i jest określany przez dowody dostarczone przez aplikację. W przypadku aplikacji WPF dostarczane dowody są lokalizacją lub strefą, z której są uruchamiane aplikacje. Urzędy certyfikacji identyfikują następujące strefy:  
  
- **Mój komputer**. Aplikacje uruchomione z komputera klienckiego (w pełni zaufane).  
  
- **Lokalny intranet**. Aplikacje uruchamiane z intranetu. (Nieco zaufane).  
  
- **Internet**. Aplikacje uruchomione z Internetu. (Najmniej zaufany).  
  
- **Zaufane witryny**. Aplikacje identyfikowane przez użytkownika jako zaufane. (Najmniej zaufany).  
  
- **Niezaufane witryny**. Aplikacje zidentyfikowane przez użytkownika jako niezaufanego. (Niezaufane).  
  
 W przypadku każdej z tych stref urzędy certyfikacji udostępniają wstępnie zdefiniowany zestaw uprawnień, który obejmuje uprawnienia zgodne z poziomem zaufania skojarzonym z każdym z nich. Należą do nich następujące elementy:  
  
- **FullTrust**. W przypadku aplikacji uruchamianych z strefy **My Computer** . Przyznano wszystkie możliwe uprawnienia.  
  
- **LocalIntranet**. W przypadku aplikacji uruchomionych ze strefy **Lokalny intranet** . Podzbiór uprawnień zapewnia średni dostęp do zasobów komputera klienckiego, w tym izolowany magazyn, nieograniczony dostęp do interfejsu użytkownika, nieograniczone okna dialogowe plików, ograniczone odbicie i ograniczony dostęp do zmiennych środowiskowych. Nie podano uprawnień do zasobów krytycznych, takich jak rejestr.  
  
- **Internet**. W przypadku aplikacji uruchamianych z strefy **Internet** lub **Zaufane witryny** . Podzbiór uprawnień zapewnia ograniczony dostęp do zasobów komputera klienckiego, w tym do magazynu izolowanego, tylko do otwierania plików i ograniczonych interfejsów użytkownika. Zasadniczo ten zestaw uprawnień izoluje aplikacje z komputera klienckiego.  
  
 Aplikacje zidentyfikowane jako pochodzące z strefy **niezaufane witryny** nie mają żadnych uprawnień przez urzędy certyfikacji. W związku z tym wstępnie zdefiniowany zestaw uprawnień nie istnieje.  
  
 Na poniższej ilustracji przedstawiono relacje między strefami, zestawami uprawnień, uprawnieniami i zasobami:  
  
 ![Diagram przedstawiający zestawy uprawnień urzędów certyfikacji.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Ograniczenia trybu piaskownicy zabezpieczeń strefy internetowej są stosowane równomiernie względem dowolnego kodu, który jest importowany przez XBAP z biblioteki systemowej, w tym WPF. Pozwala to zagwarantować, że każdy bit kodu jest zablokowany, nawet WPF. Niestety, aby można było wykonać, aplikacja XBAP musi wykonać funkcjonalność, która wymaga więcej uprawnień niż te włączone przez piaskownicę zabezpieczenia strefy internetowej.  
  
 Rozważ użycie aplikacji XBAP zawierającej następującą stronę:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Aby można było wykonać ten serwer XBAP, źródłowy kod WPF musi wykonywać więcej funkcji niż jest dostępny dla wywołującego programu XBAP, w tym:  
  
- Tworzenie uchwytu okna (HWND) do renderowania  
  
- Wysyłanie komunikatów  
  
- Ładowanie czcionki Tahoma  
  
 Z punktu widzenia zabezpieczeń, umożliwienie bezpośredniego dostępu do którejkolwiek z tych operacji w aplikacji w trybie piaskownicy będzie katastrofalne.  
  
 Na szczęście program WPF jest objęty tą sytuacją przez umożliwienie wykonywania tych operacji z podwyższonym poziomem uprawnień w imieniu aplikacji w trybie piaskownicy. Wszystkie operacje WPF są sprawdzane względem ograniczonych uprawnień do zabezpieczeń strefy internetowej domeny aplikacji XBAP, WPF (podobnie jak w przypadku innych bibliotek systemowych) przyznany zestawowi uprawnień, który obejmuje wszystkie możliwe uprawnienia.
  
 Wymaga to, aby usługa WPF otrzymała podwyższone uprawnienia, jednocześnie zapobiegając tym, aby te uprawnienia były regulowane przez zestaw uprawnień strefy internetowej domeny aplikacji hosta.  
  
 WPF wykonuje to przy użyciu metody **Assert** uprawnienia. Poniższy kod pokazuje, jak to się dzieje.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Potwierdzenie** zasadniczo uniemożliwia ograniczenie nieograniczonego uprawnień wymaganych przez program WPF przez uprawnienia strefy internetowej aplikacji XBAP.  
  
 Z perspektywy platformy WPF jest odpowiedzialna za korzystanie z poprawnego **potwierdzenia** ; nieprawidłowe użycie **potwierdzenia** może umożliwić złośliwemu kodowi podwyższenie poziomu uprawnień. W związku z tym ważne jest, aby w razie potrzeby wywołać tylko **potwierdzenie** , i upewnić się, że ograniczenia piaskownicy pozostają nienaruszone. Na przykład kod w trybie piaskownicy nie może otwierać plików losowych, ale może korzystać z czcionek. WPF umożliwia aplikacjom w trybie piaskownicy używanie funkcji czcionek przez wywoływanie metody **Assert**, a dla WPF odczytywanie plików, które zawierają te czcionki w imieniu aplikacji w trybie piaskownicy.  
  
### <a name="clickonce-deployment"></a>Wdrożenie ClickOnce  
 ClickOnce to kompleksowa technologia wdrażania dołączona do .NET Framework i integruje się z programem Visual Studio (zobacz [Zabezpieczenia technologii ClickOnce i wdrażanie](/visualstudio/deployment/clickonce-security-and-deployment) , aby uzyskać szczegółowe informacje). Autonomiczne aplikacje WPF można wdrażać za pomocą technologii ClickOnce, natomiast aplikacje hostowane w przeglądarce muszą być wdrażane przy użyciu technologii ClickOnce.  
  
 Aplikacje wdrożone przy użyciu technologii ClickOnce mają dodatkową warstwę zabezpieczeń w porównaniu z zabezpieczeniami dostępu kodu (CAS); zasadniczo aplikacje wdrożone ClickOnce żądają wymaganych uprawnień. Te uprawnienia są udzielane tylko wtedy, gdy nie przekraczają zestawu uprawnień dla strefy, z której aplikacja jest wdrażana. Zmniejszając zestaw uprawnień tylko do tych, które są niezbędne, nawet jeśli są one mniejsze niż te podane przez zestaw uprawnień strefy uruchamiania, liczba zasobów, do których aplikacja ma dostęp, jest ograniczona do minimum od zera. W związku z tym, jeśli aplikacja zostanie przejęta, potencjalne uszkodzenie komputera klienckiego jest ograniczone.  
  
### <a name="security-critical-methodology"></a>Metodologia krytyczna dla zabezpieczeń  
 Kod WPF, który używa uprawnień do włączania piaskownicy strefy internetowej dla aplikacji XBAP, musi być utrzymywany do największego możliwego stopnia inspekcji i kontroli zabezpieczeń. Aby ułatwić to wymaganie, .NET Framework zapewnia nową obsługę zarządzania kodem, który podnosi uprawnienia. Środowisko CLR umożliwia zidentyfikowanie kodu, który podnosi poziom uprawnień i oznaczenie go <xref:System.Security.SecurityCriticalAttribute>; Każdy kod, który nie jest oznaczony <xref:System.Security.SecurityCriticalAttribute>, stał się *przezroczysty* przy użyciu tej metodologii. Z drugiej strony kod zarządzany, który nie jest oznaczony za pomocą <xref:System.Security.SecurityCriticalAttribute>, nie umożliwia podniesienia uprawnień.  
  
 Metodologia krytyczna dla zabezpieczeń umożliwia organizacji kodu WPF, który podnosi uprawnienia do *jądra krytycznego*pod względem zabezpieczeń, z pozostałą resztą. Izolowanie kodu krytycznego pod względem zabezpieczeń umożliwia zespołowi inżynierów WPF skoncentrowanie się na dodatkowej analizie zabezpieczeń i kontroli źródła na jądrze o znaczeniu krytycznym powyżej i poza standardowymi praktykami w zakresie zabezpieczeń (zobacz temat [strategia zabezpieczeń WPF — Inżynieria zabezpieczeń](wpf-security-strategy-security-engineering.md)).  
  
 Należy pamiętać, że .NET Framework pozwala na rozbudowanie obszaru piaskownicy strefy internetowej XBAP przez deweloperów, umożliwiając deweloperom pisanie zestawów zarządzanych, które są oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) i wdrożone w globalnej pamięci podręcznej zestawów (GAC) użytkownika. Oznaczanie zestawu za pomocą APTCA jest wysoce poufną operacją zabezpieczeń, ponieważ umożliwia każdemu kodowi wywoływanie tego zestawu, w tym złośliwy kod z Internetu. Należy zachować szczególną ostrożność i korzystać z najlepszych rozwiązań, aby użytkownicy mogli je zaufać.  
  
## <a name="microsoft-internet-explorer-security"></a>Zabezpieczenia programu Microsoft Internet Explorer  
 Ponad zmniejszenie problemów z zabezpieczeniami i uproszczenie konfiguracji zabezpieczeń program Microsoft Internet Explorer 6 (SP2) zawiera kilka funkcji, które zwiększają bezpieczeństwo użytkowników aplikacji przeglądarki XAML (XBAP). Nacisk tych funkcji próbuje umożliwić użytkownikom większą kontrolę nad ich doświadczeniem w przeglądaniu.  
  
 Przed IE6 SP2 użytkownicy mogą podlegać dowolnym z następujących czynności:  
  
- Losowe okna podręczne.  
  
- Mylące przekierowanie skryptów.  
  
- Wiele okien dialogowych zabezpieczeń w niektórych witrynach sieci Web.  
  
 W niektórych przypadkach niezaufane witryny sieci Web próbują nakłonić użytkowników przez sfałszowanie instalacji [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] lub wielokrotne wyświetlanie okna dialogowego instalacji Microsoft ActiveX, nawet jeśli użytkownik mógł ją anulować. Korzystając z tych technik, istnieje możliwość, że znacząca liczba użytkowników została podzielona w celu podejmowania słabych decyzji, które spowodowały zainstalowanie aplikacji szpiegujących.  
  
 Program IE6 z dodatkiem SP2 zawiera kilka funkcji pozwalających wyeliminować te rodzaje problemów, które koncentrują się na koncepcji inicjacji użytkownika. Program IE6 SP2 wykrywa, kiedy użytkownik kliknie link lub element strony przed akcją, która jest znana jako *Inicjowanie użytkownika*i traktuje ją inaczej niż w przypadku wyzwolenia podobnej akcji przez skrypt na stronie. Przykładowo IE6 z dodatkiem SP2 obejmuje **wyskakujące okienko** wykrywające, kiedy użytkownik klika przycisk przed stroną tworzenia okna podręcznego. Dzięki temu program IE6 SP2 zezwala na większość wyskakujących okienek niewielkiej ilości, jednocześnie uniemożliwiając wyskakujące okienka, których użytkownicy nie proszą ani nie chcą. Zablokowane wyskakujące okienka są zalewkowane na nowym **pasku informacji**, co umożliwia użytkownikowi ręczne przesłonięcie bloku i wyświetlenie okienka wyskakującego.  
  
 Ta sama logika inicjacji użytkownika jest również stosowana do **otwierania**/**zapisywania** wierszy zabezpieczeń. Okna dialogowe instalacji ActiveX są zawsze zalewkowane na pasku informacji, chyba że reprezentuje uaktualnienie z wcześniej zainstalowanej kontrolki. Te miary łączą się, aby zapewnić użytkownikom bezpieczniejsze i bardziej kontrolowane środowisko użytkownika, ponieważ są one chronione przed lokacjami, które nękaniy w celu zainstalowania niechcianych lub złośliwych oprogramowania.  
  
 Te funkcje umożliwiają również ochronę klientów korzystających z programu IE6 SP2 do przeglądania witryn sieci Web, dzięki którym mogą oni pobierać i instalować aplikacje WPF. W szczególności jest to spowodowane tym, że program IE6 z dodatkiem SP2 oferuje lepsze środowisko użytkownika, co pozwala użytkownikom na instalowanie złośliwych lub deviousych aplikacji niezależnie od tego, jaka technologia została użyta w celu jej skompilowania, w tym WPF. WPF dodaje do tych ochrony przy użyciu technologii ClickOnce, aby ułatwić pobieranie aplikacji przez Internet. Ponieważ aplikacje przeglądarki XAML (XBAP) są wykonywane w obszarze piaskownicy zabezpieczeń strefy internetowej, można je uruchomić bezproblemowo. Z drugiej strony autonomiczne aplikacje WPF wymagają pełnego zaufania do wykonania. W przypadku tych aplikacji Technologia ClickOnce wyświetli okno dialogowe zabezpieczenia podczas procesu uruchamiania, aby powiadomić o użyciu dodatkowych wymagań w zakresie zabezpieczeń aplikacji. Jednak to musi być inicjowane przez użytkownika, a także będzie podlegać logiki zainicjowane przez użytkownika i może być anulowane.  
  
 Program Internet Explorer 7 obejmuje i rozszerza możliwości zabezpieczeń programu IE6 SP2 w ramach ciągłego zaangażowania w zabezpieczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Zabezpieczenia](security-wpf.md)
- [Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — projekt zabezpieczeń](wpf-security-strategy-security-engineering.md)
