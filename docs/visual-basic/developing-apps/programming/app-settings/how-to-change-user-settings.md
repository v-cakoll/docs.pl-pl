---
title: 'Instrukcje: Zmiana ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: c9b89459f9b443c3a447edce90fee3437bbf1b6a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410182"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Porady: zmienianie ustawień użytkownika w Visual Basic

Ustawienie użytkownika można zmienić, przypisując nową wartość do właściwości ustawienia w `My.Settings` obiekcie.  
  
 `My.Settings`Obiekt uwidacznia każde ustawienie jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia. **Zakres** ustawienia określa, czy właściwość jest tylko do odczytu: Właściwość ustawienia zakresu **aplikacji**jest tylko do odczytu, podczas gdy właściwość dla ustawienia zakresu **użytkownika**ma wartość odczyt-zapis. Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można ich programowo zmienić. Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji za pomocą **projektanta projektu** lub edytując plik konfiguracyjny aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  

 Ten przykład zmienia wartość `Nickname` Ustawienia użytkownika.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Aby ten przykład działał, aplikacja musi mieć `Nickname` ustawienie użytkownika o typie `String` .  
  
 Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji. Aby natychmiast zapisać ustawienia, wywołaj `My.Settings.Save` metodę. Aby uzyskać więcej informacji, zobacz [How to: utrwalanie ustawień użytkownika w Visual Basic](how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz też

- [My.Settings — Obiekt](../../../language-reference/objects/my-settings-object.md)
- [Porady: odczytywanie ustawień aplikacji w Visual Basic](how-to-read-application-settings.md)
- [Porady: utrwalanie ustawień użytkownika w Visual Basic](how-to-persist-user-settings.md)
- [Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
