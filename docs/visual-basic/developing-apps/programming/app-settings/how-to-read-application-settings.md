---
title: 'Instrukcje: odczytywanie ustawień aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329567"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Porady: odczytywanie ustawień aplikacji w Visual Basic

Ustawienia użytkownika można odczytać, uzyskując dostęp do właściwości ustawienia w obiekcie `My.Settings`.  
  
 Obiekt `My.Settings` uwidacznia każde ustawienie jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia. **Zakres** ustawienia wskazuje, czy właściwość jest tylko do odczytu; Właściwość dla ustawienia zakresu **aplikacji** jest tylko do odczytu, podczas gdy właściwość dla zakresu **użytkownika** ma wartość odczyt-zapis. Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Przykład  

 Ten przykład wyświetla wartość ustawienia `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Zobacz także

- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Instrukcje: Zmienianie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: utrwalanie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
