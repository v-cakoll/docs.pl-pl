---
title: 'Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 45d5fbf6fda34407d8b7eb3f959f215e7621f1c5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966948"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic
Możesz użyć `My.Settings.Save` metodę, aby utrwalić zmiany ustawień użytkownika.  
  
 Zazwyczaj aplikacje są przeznaczone do utrwalenia zmiany w ustawieniach użytkownika podczas zamykania aplikacji. Jest to spowodowane zapisywania ustawień może potrwać, w zależności od kilku czynników, w kilka sekund.  
  
 Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Mimo że można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są przeznaczone tylko do odczytu i nie można zmienić programowo. Możesz zmienić ustawienia zakres aplikacji, podczas tworzenia aplikacji, za pośrednictwem **projektanta projektu**, lub też edytując plik konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zmienia wartość `LastChanged` ustawienia użytkownika i zapisuje, które zmieniają się przez wywołanie metody `My.Settings.Save` metody.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 W tym przykładzie do pracy, aplikacja musi mieć `LastChanged` ustawienia użytkownika, typu `Date`. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Zobacz także
- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
