---
title: 'Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: ac4e1511026047ee70234d638eb8b1689dbd6056
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717860"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic
Można utworzyć siatki właściwości, dla ustawień użytkownika, definiując <xref:System.Windows.Forms.PropertyGrid> kontrola przy użyciu właściwości ustawienia użytkownika `My.Settings` obiektu.  
  
> [!NOTE]
>  W kolejności, w tym przykładzie do pracy aplikacja musi mieć jej ustawienia użytkownika skonfigurowane. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 `My.Settings` Obiekt udostępnia każdego ustawienia jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taka sama jak typ ustawienia. Ustawienie **zakres** Określa, czy właściwość jest tylko do odczytu; właściwość dla **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość dla **użytkownika**-zakresu Ustawienie to odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania. Ustawienia zakresu aplikacji można zmienić tylko wtedy, gdy tworzenie aplikacji (za pośrednictwem **projektanta projektu**) lub przez edycję pliku konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 W tym przykładzie użyto <xref:System.Windows.Forms.PropertyGrid> formantu, aby uzyskać dostęp do właściwości ustawienia użytkownika `My.Settings` obiektu. Domyślnie <xref:System.Windows.Forms.PropertyGrid> pokazuje wszystkie właściwości `My.Settings` obiektu. Jednak właściwości ustawienia użytkownika mają <xref:System.Configuration.UserScopedSettingAttribute> atrybutu. W tym przykładzie <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> właściwość <xref:System.Windows.Forms.PropertyGrid> do <xref:System.Configuration.UserScopedSettingAttribute> Aby wyświetlić jej właściwości ustawień użytkownika.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Aby dodać siatką właściwości ustawienia użytkownika  
  
1.  Dodaj **PropertyGrid** z kontrolować **przybornika** do powierzchni projektu dla aplikacji, w tym miejscu zakłada się, że `Form1`.  
  
     Domyślną nazwą formantu siatki właściwości jest `PropertyGrid1`.  
  
2.  Kliknij dwukrotnie powierzchni projektowej dla `Form1` aby otworzyć kod obsługi zdarzeń formularz ładowanie.  
  
3.  Ustaw `My.Settings` obiektu jako wybranego obiektu siatki właściwości.  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  Skonfiguruj siatki właściwości, aby pokazać tylko ustawienia użytkownika.  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  Wyświetlanie tylko ustawień zakresu aplikacji, należy użyć <xref:System.Configuration.ApplicationScopedSettingAttribute> atrybutu zamiast <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aplikacja ustawienia użytkownika są zapisywane podczas zamykania aplikacji. Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody. Aby uzyskać więcej informacji, zobacz [jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz także
- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
