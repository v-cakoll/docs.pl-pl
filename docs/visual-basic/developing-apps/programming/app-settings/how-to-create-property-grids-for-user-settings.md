---
title: 'Instrukcje: tworzenie siatek właściwości dla ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329610"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic

Siatkę właściwości dla ustawień użytkownika można utworzyć, wypełniając formant <xref:System.Windows.Forms.PropertyGrid> właściwości `My.Settings` ustawieniami użytkownika obiektu.  
  
> [!NOTE]
> Aby ten przykład działał, aplikacja musi mieć skonfigurowane ustawienia użytkownika. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Obiekt `My.Settings` udostępnia każde ustawienie jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia. Zakres ustawienia **określa,** czy właściwość jest tylko do odczytu; właściwość dla **application**-scope ustawienie jest tylko do odczytu, podczas gdy właściwość dla **użytkownika**-scope ustawienie jest odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [Obiekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania. Ustawienia zakresu aplikacji można zmienić tylko podczas tworzenia aplikacji (za pośrednictwem **projektanta projektu)** lub przez edycję pliku konfiguracyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 W tym przykładzie <xref:System.Windows.Forms.PropertyGrid> użyto formantu, aby `My.Settings` uzyskać dostęp do właściwości ustawień użytkownika obiektu. Domyślnie <xref:System.Windows.Forms.PropertyGrid> pokazuje wszystkie właściwości `My.Settings` obiektu. Jednak właściwości ustawienia użytkownika mają <xref:System.Configuration.UserScopedSettingAttribute> atrybut. W tym <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> przykładzie <xref:System.Windows.Forms.PropertyGrid> ustawia <xref:System.Configuration.UserScopedSettingAttribute> właściwość do wyświetlania tylko właściwości ustawienia użytkownika.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Aby dodać siatkę właściwości ustawień użytkownika  
  
1. Dodaj formant **PropertyGrid** z **przybornika** do powierzchni projektowej `Form1`aplikacji, zakłada się, że w tym miejscu .  
  
     Domyślną nazwą formantu właściwości-siatki jest `PropertyGrid1`.  
  
2. Kliknij dwukrotnie powierzchnię `Form1` projektową, aby otworzyć kod programu obsługi zdarzeń ładowania formularza.  
  
3. Ustaw `My.Settings` obiekt jako zaznaczony obiekt dla siatki właściwości.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Skonfiguruj siatkę właściwości, aby wyświetlała tylko ustawienia użytkownika.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Aby wyświetlić tylko ustawienia zakresu <xref:System.Configuration.ApplicationScopedSettingAttribute> aplikacji, użyj <xref:System.Configuration.UserScopedSettingAttribute>atrybutu zamiast .  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji. Aby natychmiast zapisać ustawienia, `My.Settings.Save` należy wywołać metodę. Aby uzyskać więcej informacji, zobacz [Jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz też

- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Porady: odczytywanie ustawień aplikacji w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Porady: zmienianie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Porady: utrwalanie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
