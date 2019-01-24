---
title: My.Settings — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 293e7cd6449b8a35b5e42b4823a4412e0d6a3f14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628165"
---
# <a name="mysettings-object"></a>My.Settings — Obiekt
Udostępnia właściwości i metody dostępu do ustawień aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `My.Settings` zapewnia dostęp do ustawień aplikacji i pozwala dynamicznie zapisywać oraz pobierać ustawienia właściwości i inne informacje dotyczące aplikacji. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Właściwości  
 Właściwości obiektu `My.Settings` zapewniają dostęp do ustawień aplikacji. Aby dodać lub usunąć ustawienia, należy użyć **Projektant ustawień**.  
  
 Każde ustawienie ma **nazwę**, **typ**, **zakres** i **wartość**. Ustawienia te określają, jak właściwość dostępu do każdego ustawienia wyświetla się w obiekcie `My.Settings`:  
  
-   **Nazwa** Określa nazwę właściwości.  
  
-   **Typ** Określa typ właściwości.  
  
-   **Zakres** wskazuje, czy właściwość jest tylko do odczytu. Jeśli wartością jest **aplikacja**, właściwość jest tylko do odczytu. Jeśli wartością jest **użytkownik**, ta właściwość jest do odczytu i zapisu.  
  
-   **Wartość** jest wartością domyślną właściwości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|---|---|  
|`Reload`|Ponownie ładuje ustawienia użytkownika z ostatnio zapisanymi wartościami.|  
|`Save`|Zapisuje bieżące ustawienia użytkownika.|  
  
 Obiekt `My.Settings` udostępnia zaawansowane właściwości i metody odziedziczone z klasy <xref:System.Configuration.ApplicationSettingsBase>.  
  
## <a name="tasks"></a>Zadania  
 W poniższej tabeli przedstawiono przykłady zadań z obiektem `My.Settings`.  
  
|Zadanie|Zobacz|  
|---|---|  
|Odczyt ustawienia aplikacji|[Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Zmiana ustawienia użytkownika|[Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Utrwalanie ustawień użytkownika|[Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Tworzenie siatki właściwości dla ustawień użytkownika|[Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest wyświetlana wartość ustawienia `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Configuration.ApplicationSettingsBase>
- [Instrukcje: Odczytywanie ustawień aplikacji w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Zmienianie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: Utrwalanie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
