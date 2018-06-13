---
title: 'Porady: utrwalanie ustawień użytkownika w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: e9d3ab96ffece3c7f441721b90c8c82c734b1405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584569"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Porady: utrwalanie ustawień użytkownika w Visual Basic
Można użyć `My.Settings.Save` metody do utrwalania zmian ustawień użytkownika.  
  
 Zazwyczaj aplikacje są zaprojektowane, aby utrwalić zmiany ustawień użytkownika podczas zamykania aplikacji. Jest to spowodowane zapisywania ustawień może potrwać, w zależności od wielu czynników, kilka sekund.  
  
 Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Mimo że można zmienić i zapisać wartości ustawień w zakresie użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można zmienić programowo. Możesz zmienić ustawienia zakres aplikacji, podczas tworzenia aplikacji, za pomocą **projektanta projektu**, lub poprzez edycję pliku konfiguracyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zmienia wartość `LastChanged` ustawienia użytkownika i zapisuje, które zmiany wywołując `My.Settings.Save` metody.  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 W tym przykładzie działała, aplikacja musi mieć `LastChanged` ustawienia użytkownika, typu `Date`. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Zobacz też  
 [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Porady: odczytywanie ustawień aplikacji w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Porady: Zmienianie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
