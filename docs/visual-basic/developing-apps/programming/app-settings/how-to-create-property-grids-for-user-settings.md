---
title: 'Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 4a31b44cca61caea5fdf725405646f628b5430b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968394"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic
Można utworzyć siatkę właściwości dla ustawień użytkownika, wypełniając <xref:System.Windows.Forms.PropertyGrid> kontrolkę właściwościami `My.Settings` ustawienia użytkownika obiektu.  
  
> [!NOTE]
> Aby ten przykład działał, aplikacja musi mieć skonfigurowane ustawienia użytkownika. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Obiekt uwidacznia każde ustawienie jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia. **Zakres** ustawienia określa, czy właściwość jest tylko do odczytu; Właściwość dla ustawienia zakresu **aplikacji**jest tylko do odczytu, podczas gdy właściwość dla ustawienia zakresu **użytkownika**ma wartość odczyt i zapis. Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania. Ustawienia zakresu aplikacji można zmienić tylko podczas tworzenia aplikacji (za pomocą **projektanta projektu**) lub edytując plik konfiguracyjny aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Ten przykład używa <xref:System.Windows.Forms.PropertyGrid> formantu, aby uzyskać dostęp do właściwości `My.Settings` ustawień użytkownika obiektu. Domyślnie program <xref:System.Windows.Forms.PropertyGrid> wyświetla wszystkie właściwości `My.Settings` obiektu. Jednak właściwości ustawienia użytkownika mają <xref:System.Configuration.UserScopedSettingAttribute> atrybut. Ten przykład ustawia <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> właściwość na <xref:System.Configuration.UserScopedSettingAttribute> , <xref:System.Windows.Forms.PropertyGrid> aby wyświetlić tylko właściwości ustawienia użytkownika.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Aby dodać siatkę właściwości ustawienia użytkownika  
  
1. Dodaj kontrolkę **PropertyGrid** z **przybornika** do powierzchni projektowej aplikacji, założono, że jest to możliwe `Form1`.  
  
     Domyślną nazwą kontrolki siatki właściwości jest `PropertyGrid1`.  
  
2. Kliknij dwukrotnie powierzchnię `Form1` projektową, aby otworzyć kod dla programu obsługi zdarzeń w formie załadowanej.  
  
3. `My.Settings` Ustaw obiekt jako wybrany obiekt dla siatki właściwości.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Skonfiguruj siatkę właściwości w taki sposób, aby były wyświetlane tylko ustawienia użytkownika.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Aby wyświetlić tylko ustawienia zakresu aplikacji, należy użyć <xref:System.Configuration.ApplicationScopedSettingAttribute> atrybutu <xref:System.Configuration.UserScopedSettingAttribute>zamiast.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji. Aby natychmiast zapisać ustawienia, wywołaj `My.Settings.Save` metodę. Aby uzyskać więcej informacji, zobacz [jak: Utrwalaj ustawienia użytkownika w](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Visual Basic.  
  
## <a name="see-also"></a>Zobacz także

- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: Odczytaj ustawienia aplikacji w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Zmień ustawienia użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: Utrwalanie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
