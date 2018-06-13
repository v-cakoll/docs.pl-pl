---
title: 'Porady: zmienianie ustawień użytkownika w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 2f67c3713a77c37ce43647980a9d3b17e47ba1bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591992"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Porady: zmienianie ustawień użytkownika w Visual Basic
Ustawienia użytkownika można zmienić, przypisując na nową wartość do ustawienia właściwości `My.Settings` obiektu.  
  
 `My.Settings` Obiekt ujawnia każdego ustawienia jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia i typ właściwości jest taki sam jak typ ustawienia. Ustawienie **zakresu** Określa, czy właściwość jest tylko do odczytu: właściwość **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość **użytkownika**-zakresu Ustawienie to odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Mimo że można zmienić i zapisać wartości ustawień w zakresie użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można zmienić programowo. Ustawienia zakresu aplikacji można zmienić po utworzeniu aplikacji przy użyciu **projektanta projektu** lub poprzez edycję pliku konfiguracyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zmienia wartość `Nickname` ustawienia użytkownika.  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 W tym przykładzie działała, aplikacja musi mieć `Nickname` ustawienia użytkownika, typu `String`.  
  
 Aplikacja zapisuje ustawienia użytkownika podczas zamykania aplikacji. Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody. Aby uzyskać więcej informacji, zobacz [porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz też  
 [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Porady: odczytywanie ustawień aplikacji w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
