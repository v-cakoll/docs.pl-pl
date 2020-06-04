---
title: 'Instrukcje: Odczytywanie ustawień aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 9b326341c54d652479776e3ab93a2b140f4531e0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410143"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Porady: odczytywanie ustawień aplikacji w Visual Basic

Ustawienia użytkownika można odczytać, uzyskując dostęp do właściwości ustawienia w `My.Settings` obiekcie.  
  
 `My.Settings`Obiekt uwidacznia każde ustawienie jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia. **Zakres** ustawienia wskazuje, czy właściwość jest tylko do odczytu; Właściwość dla ustawienia zakresu **aplikacji** jest tylko do odczytu, podczas gdy właściwość dla zakresu **użytkownika** ma wartość odczyt-zapis. Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Przykład  

 Ten przykład wyświetla wartość `Nickname` Ustawienia.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby ten przykład działał, aplikacja musi mieć `Nickname` ustawienie typu `String` . Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Zobacz też

- [My.Settings — Obiekt](../../../language-reference/objects/my-settings-object.md)
- [Porady: zmienianie ustawień użytkownika w Visual Basic](how-to-change-user-settings.md)
- [Porady: utrwalanie ustawień użytkownika w Visual Basic](how-to-persist-user-settings.md)
- [Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
