---
title: 'Instrukcje: zmiana ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329628"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Porady: zmienianie ustawień użytkownika w Visual Basic

Ustawienie użytkownika można zmienić, przypisując nową wartość do właściwości `My.Settings` ustawienia obiektu.  
  
 Obiekt `My.Settings` udostępnia każde ustawienie jako właściwość. Nazwa właściwości jest taka sama jak nazwa ustawienia, a typ właściwości jest taki sam jak typ ustawienia. Ustawienie **Scope** określa, czy właściwość jest tylko do odczytu: **Właściwość**dla application -scope ustawienie jest tylko do odczytu, podczas gdy właściwość dla **użytkownika**-scope ustawienie jest odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [Obiekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można zmienić programowo. Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji przy użyciu **projektanta projektu** lub edytując plik konfiguracyjny aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  

 W tym przykładzie `Nickname` zmienia wartość ustawienia użytkownika.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 W tym przykładzie do pracy `Nickname` aplikacja musi mieć `String`ustawienie użytkownika, typu .  
  
 Aplikacja zapisuje ustawienia użytkownika po zamknięciu aplikacji. Aby natychmiast zapisać ustawienia, `My.Settings.Save` należy wywołać metodę. Aby uzyskać więcej informacji, zobacz [Jak: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Zobacz też

- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Porady: odczytywanie ustawień aplikacji w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Porady: utrwalanie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
