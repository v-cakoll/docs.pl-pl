---
title: 'Instrukcje: Tworzenie ustawień aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 5cf109aec8b55650f43f07f5b303c6373df4efc7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004461"
---
# <a name="how-to-create-application-settings"></a>Instrukcje: Tworzenie ustawień aplikacji
Przy użyciu kodu zarządzanego, można tworzyć nowych ustawień aplikacji i wiązania ich z właściwościami w formularzu lub kontrolki formularza tak, aby te ustawienia są ładowane i zapisywane automatycznie w czasie wykonywania.  
  
 W poniższej procedurze należy ręcznie utworzyć klasy otoki, która pochodzi od klasy <xref:System.Configuration.ApplicationSettingsBase>. Aby tej klasy należy dodać publicznie dostępnych właściwości dla każdego ustawienia aplikacji, które chcesz udostępnić.  
  
 Można również wykonać tę procedurę za pomocą minimalnej ilości kodu w Projektancie Visual Studio.  Zobacz też [jak: Tworzenie ustawień aplikacji za pomocą projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Aby programowo utworzyć nowe ustawienia aplikacji  
  
1. Dodaj nową klasę do projektu i zmień jego nazwę. Do wykonania tej procedury, firma Microsoft będzie wywoływać tej klasy `MyUserSettings`. Zmiana definicji klasy, aby klasa pochodzi od klasy <xref:System.Configuration.ApplicationSettingsBase>.  
  
2. Zdefiniuj właściwość od tej klasy otoki dla każdego ustawienia aplikacji, potrzebujesz, a następnie Zastosuj tę właściwość z oboma <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>, w zależności od zakresu ustawienia. Aby uzyskać więcej informacji na temat zakresu ustawień, zobacz [Przegląd ustawień aplikacji](application-settings-overview.md). W razie kod powinien wyglądać następująco:  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3. W aplikacji, należy utworzyć wystąpienie tej klasy otoki. Będzie najczęściej od prywatnej składowej formularza głównego. Po zdefiniowaniu klasy należy powiązać go z właściwością; w tym przypadku <xref:System.Windows.Forms.Form.BackColor%2A> właściwości formularza. Można to zrobić do formularza `Load` programu obsługi zdarzeń.  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4. Jeśli podasz sposób, aby zmienić ustawienia w czasie wykonywania, należy zapisać bieżące ustawienia użytkownika na dysku w przypadku, gdy formularz zostanie zamknięty, w przeciwnym razie te zmiany zostaną utracone.  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Możesz pomyślnie utworzono nowe ustawienie aplikacji i powiązany określonej właściwości.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Domyślny dostawca ustawień <xref:System.Configuration.LocalFileSettingsProvider>, będzie nadal występował, informacje w plikach konfiguracji jako zwykły tekst. Ogranicza to zabezpieczeń w celu zabezpieczenia dostępu do plików, które są dostarczane przez system operacyjny dla bieżącego użytkownika. W związku z tym należy uważać, z informacjami przechowywanymi w plikach konfiguracji. Na przykład jeden typowym celem zastosowania ustawienia aplikacji jest przechowywanie parametrów połączenia, prowadzące do aplikacji w magazynie danych. Jednak ze względu na problemy dotyczące zabezpieczeń, takich ciągów nie może zawierać hasła. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Przegląd ustawień aplikacji](application-settings-overview.md)
- [Instrukcje: Sprawdzanie poprawności ustawień aplikacji](how-to-validate-application-settings.md)
