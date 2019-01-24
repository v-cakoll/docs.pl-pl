---
title: 'Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 032e06e674f2298d68f879f3ad474c79e3ff02db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659500"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic
Ustawienia użytkownika może być odczytany przez uzyskiwanie dostępu do właściwości ustawienia na `My.Settings` obiektu.  
  
 `My.Settings` Obiekt udostępnia każdego ustawienia jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taka sama jak typ ustawienia. Ustawienie **zakres** wskazuje, czy właściwość jest tylko do odczytu; właściwość dla **aplikacji** ustawienie zakresu jest tylko do odczytu, podczas właściwość dla **użytkownika** ustawienie zakresu jest do odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest wyświetlana wartość ustawienia `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Zobacz także
- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
