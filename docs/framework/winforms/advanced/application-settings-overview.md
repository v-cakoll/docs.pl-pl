---
title: "Przegląd ustawień aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f74595ce672079db69fd36fb2b2eb982bc90b448
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-overview"></a>Przegląd ustawień aplikacji
W tym temacie omówiono sposób tworzenia i przechowywania danych ustawienia w imieniu użytkowników i aplikacji.  
  
 Funkcja ustawienia aplikacji formularzy systemu Windows można łatwo tworzyć, przechowywać i Obsługa niestandardowych aplikacji i preferencji użytkownika na komputerze klienckim. Ustawienia aplikacji formularzy systemu Windows można przechowywać nie tylko dane aplikacji, takie jak parametry połączenia bazy danych, ale również dane specyficzne dla użytkownika, takie jak preferencje użytkownika. Przy użyciu programu Visual Studio lub niestandardowy kod zarządzany, możesz utworzyć nowe ustawienia, je z odczytu i zapisu, je na dysk, powiązać właściwości na formularzach i sprawdzanie poprawności danych ustawienia przed ładowania i zapisywania.  
  
 Ustawienia aplikacji umożliwia deweloperom zapisanie stanu w aplikacjach za pomocą bardzo mało kodu niestandardowego, a nie zastępuje właściwości dynamicznych w poprzednich wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Ustawienia aplikacji zawiera wiele ulepszeń za pośrednictwem właściwości dynamiczne, które są tylko do odczytu, późnym wiązaniem i wymaga więcej programowania niestandardowych. Klasy właściwości dynamicznych zatrzymane w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], ale są one tylko klasy powłoki alokowane opakowujących klasy ustawienia aplikacji.  
  
## <a name="what-are-application-settings"></a>Co to są ustawienia aplikacji?  
 Aplikacje Windows Forms często będą wymagać danych, która jest krytyczne dla działania aplikacji, ale które nie chcesz dołączyć bezpośrednio w kodzie aplikacji. Jeśli aplikacja korzysta z usługi sieci Web lub serwer bazy danych, warto przechowywać tych informacji w osobnym pliku, tak, aby można go w przyszłości zmienić bez ponownego kompilowania. Podobnie aplikacje mogą wymagać przechowywania danych, które są specyficzne dla bieżącego użytkownika. Większość aplikacji, na przykład mieć preferencje użytkownika, które dostosować wygląd i działanie aplikacji.  
  
 Adresy ustawienia aplikacji zarówno musi zapewniając łatwy sposób przechowywania ustawień zarówno zakresu aplikacji i zakresu użytkownika na komputerze klienckim. Przy użyciu programu Visual Studio lub edytora kodu, zdefiniuj ustawienie dla danej właściwości, określając jej nazwę, typ danych i zakresu (aplikacji lub użytkownika). Można nawet umieścić powiązane ustawienia na grupy o nazwie łatwiejsze i czytelności. Po zdefiniowaniu, te ustawienia są utrwalane i odczytu do pamięci automatycznie w czasie wykonywania. Architektura obsługująca dodatki umożliwia mechanizmu stanu trwałego zostanie zmieniony, ale domyślnie jest używana w lokalnym systemie plików.  
  
 Ustawienia aplikacji polega na trwałych danych jako XML do innej konfiguracji (config) plików, odpowiednie do tego, czy ustawienie jest zakresu aplikacji lub zakresu użytkownika. W większości przypadków ustawienia zakresu aplikacji są tylko do odczytu. ponieważ są one informacje o programie, zwykle nie należy je zastąpić. Z kolei ustawień z zakresu użytkownika może odczytywać i zapisane bezpiecznie w czasie wykonywania, nawet wtedy, gdy aplikacja działa w częściowej relacji zaufania. Aby uzyskać więcej informacji o częściowej relacji zaufania, zobacz [zabezpieczeń w formularzach systemu Windows-omówienie](../../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
 Ustawienia są przechowywane jako fragmenty XML w plikach konfiguracji. Ustawienia zakresu aplikacji są reprezentowane przez `<application.Settings>` elementu i zazwyczaj są umieszczane w *aplikacji*. exe.config, gdzie *aplikacji* to nazwa głównego pliku wykonywalnego. Ustawienia zakresu użytkownika są reprezentowane przez `<userSettings>` elementu i są umieszczane w *użytkownika*.config, gdzie *użytkownika* jest nazwą użytkownika osoby obecnie uruchomiona aplikacja. Należy wdrożyć *aplikacji*. exe.config plików z aplikacji; ustawienia utworzy architektura *użytkownika*plikach .config na czas żądanie pierwsza aplikacja zapisuje ustawienia dla tego użytkownika. Można również zdefiniować `<userSettings>` zablokować w *aplikacji*. exe.config o podanie wartości domyślne ustawień z zakresu użytkownika.  
  
 Formanty niestandardowe można także zapisać swoje własne ustawienia zaimplementowanie <xref:System.Configuration.IPersistComponentSettings> interfejsu, który ujawnia <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> metody. Formularze systemu Windows <xref:System.Windows.Forms.ToolStrip> formant implementuje ten interfejs, aby zapisać pozycji pasków narzędzi i elementy paska narzędzi między sesjami aplikacji. Aby uzyskać więcej informacji o kontrolkach niestandardowych i ustawienia aplikacji, zobacz [ustawienia aplikacji dotyczące kontrolek niestandardowych](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md).  
  
## <a name="limitations-of-application-settings"></a>Ograniczenia dotyczące ustawień aplikacji  
 Nie można użyć ustawienia aplikacji w niezarządzanej aplikacji, który jest hostem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Ustawienia nie będzie działać w środowiskach, takich jak Visual Studio dodatków, C++ dla programu Microsoft Office, kontrolować hosting w programu Internet Explorer lub Microsoft Outlook dodatków i projektów.  
  
 Obecnie nie można powiązać z niektórych właściwości w formularzach systemu Windows. Najlepszym przykładem jest <xref:System.Windows.Forms.Form.ClientSize%2A> właściwość, jako powiązania do tej właściwości może spowodować nieprzewidziane zachowanie w czasie wykonywania. Można zwykle obejścia tych problemów przez zapisywanie i ładowanie te ustawienia programowo.  
  
 Ustawienia aplikacji ma nie wbudowane funkcje automatycznie szyfrowania informacji. Informacje związane z zabezpieczeniami, takich jak hasła bazy danych, nigdy nie należy przechowywać w postaci zwykłego tekstu. Jeśli chcesz przechowywać tych informacji poufnych, Deweloper aplikacji jest odpowiedzialny za zapewnienie, że jest to bezpieczne. Jeśli chcesz przechowywać parametry połączenia, zaleca się Użyj zintegrowanych zabezpieczeń systemu Windows i odwołać nie Koduj haseł do adresu URL. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
## <a name="getting-started-with-application-settings"></a>Wprowadzenie do ustawień aplikacji  
 Jeśli używasz programu Visual Studio można zdefiniować ustawienia w obrębie Projektant formularzy systemu Windows, przy użyciu **(ApplicationSettings)** właściwości w **właściwości** okna. Podczas definiowania ustawień w ten sposób programu Visual Studio automatycznie tworzy klasę niestandardowy zarządzany otok, co umożliwia skojarzenie każdego ustawienia właściwości klasy. Visual Studio również odpowiada on za powiązania ustawienie właściwości formularza lub kontrolki, tak, aby ustawienia kontroli zostaną przywrócone automatycznie po jego formularza jest wyświetlany i zapisane automatycznie, gdy formularz jest zamknięty.  
  
 Jeśli chcesz bardziej szczegółową kontrolę nad ustawienia, można zdefiniować klasy otoki ustawienia własne niestandardowe aplikacje. Jest to osiągane przez wyprowadzanie klasy z <xref:System.Configuration.ApplicationSettingsBase>, dodawanie właściwości, która odpowiada do każdego ustawienia, a stosowanie atrybutów specjalne tych właściwości. Aby uzyskać więcej informacji o tworzeniu klasy otoki, zobacz [Architektura ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
 Można również użyć <xref:System.Windows.Forms.Binding> klasę, aby powiązać programowo ustawienia właściwości formularzy i kontrolek.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Instrukcje: sprawdzanie poprawności ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)  
 [Zarządzanie ustawieniami aplikacji (.NET)](http://msdn.microsoft.com/library/35254321-ad14-47d9-b8c6-39ab3203c5d9)  
 [Instrukcje: czytanie ustawień w czasie wykonywania w języku C#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [Używanie ustawień aplikacji i ustawień użytkownika](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Architektura ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Ustawienia aplikacji dotyczące kontrolek niestandardowych](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)
