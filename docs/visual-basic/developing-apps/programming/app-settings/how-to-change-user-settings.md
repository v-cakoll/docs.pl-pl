---
title: 'Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 3cf50f838124539dc774574cd1ad0b629d01a9ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688201"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic
Można zmienić ustawienia użytkownika, przypisując nową wartość do ustawienia właściwości na `My.Settings` obiektu.  
  
 `My.Settings` Obiekt udostępnia każdego ustawienia jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taka sama jak typ ustawienia. Ustawienie **zakres** Określa, czy właściwość jest tylko do odczytu: Właściwość dla **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość dla **użytkownika**— ustawienie zakresu jest odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Mimo że można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są przeznaczone tylko do odczytu i nie można zmienić programowo. Ustawienia zakresu aplikacji można zmienić po utworzeniu aplikacji za pomocą **projektanta projektu** lub też edytując plik konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zmienia wartość `Nickname` ustawienia użytkownika.  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 W tym przykładzie do pracy, aplikacja musi mieć `Nickname` ustawienia użytkownika, typu `String`.  
  
 Aplikacja ustawienia użytkownika są zapisywane podczas zamykania aplikacji. Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody. Aby uzyskać więcej informacji, zobacz [jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz także
- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
