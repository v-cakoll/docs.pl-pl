---
title: Przegląd ustawień aplikacji
ms.date: 03/30/2017
f1_keywords:
- ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
ms.openlocfilehash: eac8c932e9f661933f943a507485a170dc6b6132
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713071"
---
# <a name="application-settings-overview"></a>Przegląd ustawień aplikacji
W tym temacie omówiono sposób tworzenia i przechowywania danych ustawień w imieniu użytkowników i aplikacji.  
  
 Funkcja ustawienia aplikacji Windows Forms ułatwia tworzenie i przechowywanie i Obsługa niestandardowych aplikacji i preferencji użytkowników na komputerze klienckim. Za pomocą ustawień aplikacji Windows Forms można przechowywać nie tylko dane aplikacji, takie jak parametry połączenia bazy danych, ale również dane specyficzne dla użytkownika, takie jak preferencje użytkownika. Przy użyciu programu Visual Studio lub niestandardowy zarządzany kod, możesz utworzyć nowe ustawienia, odczytać ich z i zapisanie ich do dysku, powiązać je z właściwościami w formularzach i sprawdzanie poprawności ustawień danych przed ładowania i zapisywania.  
  
 Ustawienia aplikacji pozwala deweloperom na zapisanie stanu w aplikacjach za pomocą bardzo mało kodu niestandardowego i zastępuje właściwości dynamicznych w poprzednich wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Ustawienia aplikacji zawiera wiele ulepszeń za pośrednictwem właściwości dynamicznych, które są tylko do odczytu, z późnym wiązaniem i wymagają więcej niestandardowych programów. Właściwości dynamiczne klasy zatrzymane w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], ale są one po prostu klasy powłoki, które alokowane opakowywania klas ustawień aplikacji.  
  
## <a name="what-are-application-settings"></a>Co to są ustawienia aplikacji?  
 Aplikacje Windows Forms często będą wymagać danych jest krytyczne dla działania aplikacji, ale którego nie chcesz dołączyć bezpośrednio w kodzie aplikacji. Jeśli aplikacja korzysta z usługi sieci Web lub serwera bazy danych, warto przechowywać tych informacji w oddzielnym pliku, aby można go w przyszłości zmienić bez ponownego kompilowania. Podobnie Twoje aplikacje mogą wymagać przechowywania danych, które są specyficzne dla bieżącego użytkownika. Większość aplikacji, na przykład mieć preferencje użytkownika, które dostosować wygląd i zachowanie aplikacji.  
  
 Adresy ustawienia aplikacji zarówno musi, zapewniając łatwy sposób przechowywania ustawień o zakresie aplikacji i zakresu użytkownika na komputerze klienckim. Za pomocą programu Visual Studio lub Edytor kodu, zdefiniować ustawienia dla danej właściwości, określając jej nazwę, typ danych i zakresu (aplikacji lub użytkownika). Można nawet umieścić powiązane ustawienia do nazwanych grup do użytku łatwiejsze i czytelności. Po zdefiniowaniu te ustawienia są zachowywane i odczytywać je do pamięci automatycznie w czasie wykonywania. Architektura obsługująca dodatki umożliwia mechanizmu stanu trwałego, który ma zostać zmieniony, ale domyślnie jest używany w lokalnym systemie plików.  
  
 Ustawienia aplikacji polega na utrwalanie danych jako XML do innej konfiguracji (.config) plików, odpowiedniego do tego, czy ustawienie jest o zakresie aplikacji lub użytkownika o określonym zakresie. W większości przypadków ustawień o zakresie aplikacji są tylko do odczytu. ponieważ są one informacje o programie, zazwyczaj nie należy je zastąpić. Z drugiej strony ustawień zakresu użytkownika może odczytywać i zapisane bezpiecznie w czasie wykonywania, nawet wtedy, gdy aplikacja działa w częściowej relacji zaufania. Aby uzyskać więcej informacji na temat częściowej relacji zaufania, zobacz [zabezpieczeń w Windows Forms — omówienie](../security-in-windows-forms-overview.md).  
  
 Ustawienia są przechowywane jako fragmenty XML w plikach konfiguracji. Ustawienia w zakresie aplikacji są reprezentowane przez `<application.Settings>` element i zazwyczaj są umieszczane w *aplikacji*. exe.config, gdzie *aplikacji* to nazwa głównego pliku wykonywalnego. Ustawienia z zakresu użytkownika są reprezentowane przez `<userSettings>` elementu i są umieszczane w *użytkownika*.config, gdzie *użytkownika* to nazwa użytkownika osoby, aktualnie uruchomiona jest aplikacja. Należy wdrożyć *aplikacji*. exe.config plików za pomocą aplikacji; ustawienia utworzy architektury *użytkownika*.config plików na żądanie pierwszego czasu aplikacja zapisuje ustawienia dla tego użytkownika. Można również definiować `<userSettings>` blokowania w ramach *aplikacji*. exe.config w celu określenia wartości domyślnych ustawień zakresu użytkownika.  
  
 Kontrolki niestandardowe można także zapisać własne ustawienia, implementując <xref:System.Configuration.IPersistComponentSettings> interfejsu, który ujawnia <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> metody. Formularze Windows <xref:System.Windows.Forms.ToolStrip> kontrolka implementuje ten interfejs, aby zapisać pozycji pasków narzędzi i elementów paska narzędzi, między sesjami aplikacji. Aby dowiedzieć się więcej o kontrolkach niestandardowych i ustawienia aplikacji, zobacz [ustawienia aplikacji dotyczące kontrolek niestandardowych](application-settings-for-custom-controls.md).  
  
## <a name="limitations-of-application-settings"></a>Ograniczenia dotyczące ustawień aplikacji  
 Nie można użyć ustawienia aplikacji w niezarządzanej aplikacji, który jest hostem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Ustawienia nie będą działać w takich środowiskach jak Visual Studio dodatki, Microsoft Office w języku C++ kontrolować hosting w programie Internet Explorer lub dodatków programu Microsoft Outlook i projektów.  
  
 Obecnie nie można powiązać z niektórych właściwości w formularzach Windows Forms. Najlepszym przykładem jest <xref:System.Windows.Forms.Form.ClientSize%2A> właściwości jako powiązania do tej właściwości mogłoby spowodować nieprzewidywalne zachowanie w czasie wykonywania. Można zwykle obejścia tych problemów, zapisywanie i ładowanie te ustawienia programowo.  
  
 Ustawienia aplikacji nie ma żadnych wbudowanych funkcji do automatycznego szyfrowania informacji. Nigdy nie przechowuj informacji związanych z zabezpieczeniami, takie jak hasła bazy danych w postaci zwykłego tekstu. Jeśli chcesz przechowywać tych informacji poufnych, Deweloper aplikacji jesteś odpowiedzialny za upewnienie się, że jest bezpieczne. Jeśli chcesz przechowywać parametry połączenia, zaleca się używać zabezpieczeń zintegrowanych Windows i nie zastosuje poważniejsze niezmiennych haseł do adresu URL. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../data/adonet/code-access-security.md).  
  
## <a name="getting-started-with-application-settings"></a>Wprowadzenie do ustawień aplikacji  
 Jeśli używasz programu Visual Studio, można zdefiniować ustawienia w obrębie za pomocą programu Windows Forms Designer **(ApplicationSettings)** właściwość **właściwości** okna. Podczas definiowania ustawień w ten sposób program Visual Studio automatycznie tworzy klasy niestandardowej otoka zarządzana, która kojarzy każde ustawienie właściwości klasy. Program Visual Studio zajmie również powiązania ustawienie właściwości formularza lub formantu, aby ustawienia kontroli zostaną przywrócone automatycznie jej formularz jest wyświetlany, gdy zapisywane automatycznie, gdy formularz jest zamknięty.  
  
 Jeśli chcesz bardziej szczegółową kontrolę nad ustawienia, można zdefiniować własne klasy otoki ustawień niestandardowych aplikacji. Jest to osiągane przez wyprowadzanie klasy z <xref:System.Configuration.ApplicationSettingsBase>, dodając właściwość, która odnosi się do każdego ustawienia i stosowanie specjalnych atrybutów do tych właściwości. Aby uzyskać szczegółowe informacje o tworzeniu klas otoki, zobacz [Architektura ustawień aplikacji](application-settings-architecture.md).  
  
 Można również użyć <xref:System.Windows.Forms.Binding> klasy ustawienia programowo można powiązać właściwości formularzy i kontrolek.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- <xref:System.Configuration.IPersistComponentSettings>
- [Instrukcje: Sprawdzanie poprawności ustawień aplikacji](how-to-validate-application-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
- [Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#](how-to-read-settings-at-run-time-with-csharp.md)
- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Architektura ustawień aplikacji](application-settings-architecture.md)
- [Ustawienia aplikacji dotyczące kontrolek niestandardowych](application-settings-for-custom-controls.md)
