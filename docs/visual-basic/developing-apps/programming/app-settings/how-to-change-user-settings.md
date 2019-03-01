---
title: 'Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 4e93dbf453b831bb28707250466ea928bfe9a716
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976385"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic
Można zmienić ustawienia użytkownika, przypisując nową wartość do ustawienia właściwości na `My.Settings` obiektu.  
  
 `My.Settings` Obiekt udostępnia każdego ustawienia jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taka sama jak typ ustawienia. Ustawienie **zakres** Określa, czy właściwość jest tylko do odczytu: Właściwość dla **aplikacji**— ustawienie zakresu jest tylko do odczytu, podczas właściwość dla **użytkownika**— ustawienie zakresu jest odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Mimo że można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są przeznaczone tylko do odczytu i nie można zmienić programowo. Ustawienia zakresu aplikacji można zmienić po utworzeniu aplikacji za pomocą **projektanta projektu** lub też edytując plik konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zmienia wartość `Nickname` ustawienia użytkownika.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 W tym przykładzie do pracy, aplikacja musi mieć `Nickname` ustawienia użytkownika, typu `String`.  
  
 Aplikacja ustawienia użytkownika są zapisywane podczas zamykania aplikacji. Aby zapisać ustawienia natychmiast, należy wywołać `My.Settings.Save` metody. Aby uzyskać więcej informacji, zobacz [jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz także
- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
