---
title: "Porady: tworzenie ustawień aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 481239b472ced5ef6251b665dad16e83a170607d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-application-settings"></a>Porady: tworzenie ustawień aplikacji
Za pomocą kodu zarządzanego, można tworzyć nowe ustawienia aplikacji i powiązać je z właściwości formularza lub kontrolki formularza, aby te ustawienia są ładowane i automatycznie zapisywane w czasie wykonywania.  
  
 W poniższej procedurze ręcznie utworzyć klasy otoki, która jest pochodną <xref:System.Configuration.ApplicationSettingsBase>. Do tej klasy można dodać dostępny publicznie element właściwości dla każdego ustawienia aplikacji, które chcesz udostępnić.  
  
 Można również wykonać tę procedurę przy użyciu minimalnego kodu w projektancie programu Visual Studio.  Zobacz też [porady: tworzenie aplikacji ustawienia przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Aby utworzyć nowe ustawienia aplikacji programowo  
  
1.  Dodaj nową klasę do projektu i zmień jego nazwę. Do wykonania tej procedury, firma Microsoft będzie wywoływać tej klasy `MyUserSettings`. Zmień definicję klasy, tak aby pochodną klasy <xref:System.Configuration.ApplicationSettingsBase>.  
  
2.  Definiuje właściwości od tej klasy otoki dla każdego ustawienia aplikacji, potrzebujesz i zastosować tej właściwości przy użyciu jednej <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>, w zależności od zakresu ustawienia. Aby uzyskać więcej informacji na temat zakres ustawień, zobacz [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md). W razie kod powinien wyglądać następująco:  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  Utwórz wystąpienie tej klasy otoki w aplikacji. Zwykle będzie prywatnego elementu członkowskiego formularza głównego. Teraz, gdy zdefiniowano klasy, należy powiązać go z właściwością; w takim przypadku <xref:System.Windows.Forms.Form.BackColor%2A> właściwości formularza. Można to zrobić w formularza `Load` obsługi zdarzeń.  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  Jeśli podasz sposób, aby zmienić ustawienia w czasie wykonywania, należy zapisać bieżące ustawienia użytkownika na dysku po zamknięciu formularza, w przeciwnym razie te zmiany zostaną utracone.  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Teraz pomyślnie utworzono nowe ustawienie aplikacji i powiązany określonej właściwości.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Domyślny dostawca ustawień <xref:System.Configuration.LocalFileSettingsProvider>, będzie nadal występował, informacje w plikach konfiguracji jako zwykły tekst. To ogranicza zabezpieczeń w celu zabezpieczenia dostępu do plików obsługiwanych przez system operacyjny dla bieżącego użytkownika. W związku z tym należy uważać z informacjami przechowywanymi w plikach konfiguracji. Na przykład jednym z typowych zastosowań ustawienia aplikacji jest przechowywanie parametrów połączenia, wskazujące magazynu danych aplikacji. Jednak ze względu na problemy z zabezpieczeniami, takich ciągów nie może zawierać hasła. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Porady: Sprawdzanie poprawności ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
