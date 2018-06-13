---
title: 'Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: c03e7c6138633287506ff01128a1e2acb321b02d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590988"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic
Siatki właściwości dla ustawień użytkownika można tworzyć przy wprowadzaniu <xref:System.Windows.Forms.PropertyGrid> formantu użytkownika ustawienie właściwości `My.Settings` obiektu.  
  
> [!NOTE]
>  W kolejności, w tym przykładzie działała aplikacja musi mieć jego skonfigurowane ustawienia użytkownika. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Obiekt ujawnia każdego ustawienia jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia i typ właściwości jest taki sam jak typ ustawienia. Ustawienie **zakresu** Określa, czy właściwość jest tylko do odczytu; właściwość **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość **użytkownika**-zakresu Ustawienie to odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania. Ustawienia zakresu aplikacji można zmienić tylko wtedy, gdy tworzenie aplikacji (za pośrednictwem **projektanta projektu**) lub poprzez edycję pliku konfiguracyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 W tym przykładzie użyto <xref:System.Windows.Forms.PropertyGrid> formantu, aby uzyskać dostęp do właściwości ustawienia użytkownika `My.Settings` obiektu. Domyślnie <xref:System.Windows.Forms.PropertyGrid> zawiera wszystkie właściwości `My.Settings` obiektu. Jednak ustawienia użytkownika właściwości mają <xref:System.Configuration.UserScopedSettingAttribute> atrybutu. W tym przykładzie <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> właściwość <xref:System.Windows.Forms.PropertyGrid> do <xref:System.Configuration.UserScopedSettingAttribute> do wyświetlenia tylko właściwości ustawień użytkownika.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Aby dodać siatki właściwości ustawienia użytkownika  
  
1.  Dodaj **PropertyGrid** kontrolować z **przybornika** na powierzchnię projektu dla aplikacji, w tym miejscu zakłada się, że `Form1`.  
  
     Domyślna nazwa formantu siatki właściwości to `PropertyGrid1`.  
  
2.  Kliknij dwukrotnie powierzchnię projektu dla `Form1` otworzyć kodu dla obsługi zdarzeń ładowania formularza.  
  
3.  Ustaw `My.Settings` obiektu jako obiektu wybranego w siatce właściwości.  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  Skonfiguruj siatki właściwości, aby wyświetlić tylko ustawienia użytkownika.  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  Aby wyświetlić tylko ustawienia zakres aplikacji, należy użyć <xref:System.Configuration.ApplicationScopedSettingAttribute> atrybutu zamiast <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aplikacja zapisuje ustawienia użytkownika podczas zamykania aplikacji. Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody. Aby uzyskać więcej informacji, zobacz [porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz też  
 [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Porady: odczytywanie ustawień aplikacji w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Porady: Zmienianie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
