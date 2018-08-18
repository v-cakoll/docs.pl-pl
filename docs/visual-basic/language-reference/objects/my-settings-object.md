---
title: My.Settings — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 54176ae6706311b17227c7dc21a5060c9b369753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603035"
---
# <a name="mysettings-object"></a>My.Settings — Obiekt
Udostępnia właściwości i metody dostępu do ustawień aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `My.Settings` zapewnia dostęp do ustawień aplikacji i pozwala dynamicznie zapisywać i pobierać ustawienia właściwości i inne informacje dotyczące aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Właściwości  
 Właściwości obiektu `My.Settings` zapewniają dostęp do ustawień aplikacji. Aby dodać lub usunąć ustawienia, należy użyć **projektanta ustawień**.  
  
 Każde ustawienie ma **nazwę**, **typ**, **zakres**, i **wartość**, i te ustawienia określają, jak pojawia się właściwość dostępu do każdego ustawienia w obiekcie `My.Settings`:  
  
-   **Nazwa** Określa nazwę właściwości.  
  
-   **Typ** Określa typ właściwości.  
  
-   **Zakres** wskazuje, czy właściwość jest tylko do odczytu. Jeśli wartością jest **aplikacja**, właściwość jest tylko do odczytu; jeśli wartością jest **użytkownik**, ta właściwość jest do odczytu / zapisu.  
  
-   **Wartość** jest wartością domyślną właściwości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|---|---|  
|`Reload`|Ponownie ładuje ustawienia użytkownika z ostatnio zapisanymi wartościami.|  
|`Save`|Zapisuje bieżące ustawienia użytkownika.|  
  
 Obiekt `My.Settings` udostępnia zaawansowane właściwości i metody odziedziczone z klasy <xref:System.Configuration.ApplicationSettingsBase>.  
  
## <a name="tasks"></a>Zadania  
 W poniższej tabeli przedstawiono przykłady dotyczące zadań obiektu `My.Settings`.  
  
|Zadanie|Zobacz|  
|---|---|  
|Odczyt ustawień aplikacji|[Porady: odczytywanie ustawień aplikacji w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Zmiana ustawienia użytkownika|[Porady: zmiana ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Utrwalanie ustawień użytkownika|[Porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Tworzenie siatki właściwości dla ustawień użytkownika|[Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyświetlono wartość ustawienia `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 Aby ten przykład zadziałał, aplikacja musi mieć ustawienie `Nickname` typu `String`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [Porady: odczytywanie ustawień aplikacji w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Porady: zmiana ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
 
