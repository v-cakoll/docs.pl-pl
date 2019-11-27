---
title: 'Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329610"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic

Można utworzyć siatkę właściwości dla ustawień użytkownika, wypełniając kontrolkę <xref:System.Windows.Forms.PropertyGrid> za pomocą właściwości ustawienia użytkownika obiektu `My.Settings`.  
  
> [!NOTE]
> Aby ten przykład działał, aplikacja musi mieć skonfigurowane ustawienia użytkownika. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Obiekt `My.Settings` uwidacznia każde ustawienie jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia. **Zakres** ustawienia określa, czy właściwość jest tylko do odczytu; Właściwość dla ustawienia zakresu **aplikacji**jest tylko do odczytu, podczas gdy właściwość dla ustawienia zakresu **użytkownika**ma wartość odczyt i zapis. Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Nie można zmienić ani zapisać wartości ustawień zakresu aplikacji w czasie wykonywania. Ustawienia zakresu aplikacji można zmienić tylko podczas tworzenia aplikacji (za pomocą **projektanta projektu**) lub edytując plik konfiguracyjny aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Ten przykład używa formantu <xref:System.Windows.Forms.PropertyGrid>, aby uzyskać dostęp do właściwości ustawień użytkownika obiektu `My.Settings`. Domyślnie <xref:System.Windows.Forms.PropertyGrid> wyświetla wszystkie właściwości obiektu `My.Settings`. Jednak właściwości ustawienia użytkownika mają atrybut <xref:System.Configuration.UserScopedSettingAttribute>. Ten przykład ustawia właściwość <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> <xref:System.Windows.Forms.PropertyGrid>, aby <xref:System.Configuration.UserScopedSettingAttribute> wyświetlić tylko właściwości ustawienia użytkownika.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Aby dodać siatkę właściwości ustawienia użytkownika  
  
1. Dodaj kontrolkę **PropertyGrid** z **przybornika** do powierzchni projektowej aplikacji, założono tutaj, aby była `Form1`.  
  
     Domyślna nazwa kontrolki siatki właściwości jest `PropertyGrid1`.  
  
2. Kliknij dwukrotnie powierzchnię projektu dla `Form1`, aby otworzyć kod dla programu obsługi zdarzeń w ramach ładowania formularza.  
  
3. Ustaw `My.Settings` obiekt jako wybrany obiekt dla siatki właściwości.  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. Skonfiguruj siatkę właściwości w taki sposób, aby były wyświetlane tylko ustawienia użytkownika.  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > Aby wyświetlić tylko ustawienia zakresu aplikacji, należy użyć atrybutu <xref:System.Configuration.ApplicationScopedSettingAttribute>, a nie <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  

 Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji. Aby natychmiast zapisać ustawienia, wywołaj metodę `My.Settings.Save`. Aby uzyskać więcej informacji, zobacz [How to: utrwalanie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz także

- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: odczytywanie ustawień aplikacji w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Zmienianie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: utrwalanie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
