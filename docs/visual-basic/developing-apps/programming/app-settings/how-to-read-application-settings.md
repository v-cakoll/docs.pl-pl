---
title: "Porady: odczytywanie ustawień aplikacji w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Porady: odczytywanie ustawień aplikacji w Visual Basic
Ustawienia użytkownika może być odczytany przez uzyskiwanie dostępu do ustawiania właściwości na `My.Settings` obiektu.  
  
 `My.Settings` Obiekt ujawnia każdego ustawienia jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia i typ właściwości jest taki sam jak typ ustawienia. Tego ustawienia **zakresu** wskazuje, czy właściwość jest tylko do odczytu; właściwość **aplikacji** ustawienie zakresu jest tylko do odczytu, podczas właściwość **użytkownika** zakres ustawienie jest do odczytu / zapisu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyświetlono wartości `Nickname` ustawienie.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 W tym przykładzie działała, aplikacja musi mieć `Nickname` ustawienia typu `String`. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Zobacz też  
 [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Porady: Zmienianie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
