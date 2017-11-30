---
title: "My.Settings — Obiekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords: My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f744460f8ea6c6c7f5c8c5e1658bd357e910def
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mysettings-object"></a>My.Settings — Obiekt
Udostępnia właściwości i metod dostępu do ustawień aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 `My.Settings` Obiektu zapewnia dostęp do ustawień aplikacji i pozwala na dynamicznie przechowywać i pobierać ustawienia właściwości i inne informacje dotyczące aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Właściwości  
 Właściwości `My.Settings` obiektu zapewniają dostęp do ustawień aplikacji. Aby dodać lub usunąć ustawienia, należy użyć **projektanta ustawień**.  
  
 Każdy ma **nazwa**, **typu**, **zakres**, i **wartość**, i te ustawienia określają, jak właściwości każdego ustawienia dostępu do zostanie wyświetlony w `My.Settings` obiektu:  
  
-   **Nazwa** Określa nazwę właściwości.  
  
-   **Typ** Określa typ właściwości.  
  
-   **Zakres** wskazuje, czy właściwość jest tylko do odczytu. Jeśli wartość jest **aplikacji**, właściwość jest tylko do odczytu; Jeśli wartość jest **użytkownika**, ta właściwość jest do odczytu / zapisu.  
  
-   **Wartość** jest wartością domyślną właściwości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|---|---|  
|`Reload`|Ponownie ładuje ustawienia użytkownika z ostatnio zapisane wartości.|  
|`Save`|Zapisuje bieżące ustawienia użytkownika.|  
  
 `My.Settings` Obiektu udostępnia zaawansowane właściwości i metod odziedziczone <xref:System.Configuration.ApplicationSettingsBase> klasy.  
  
## <a name="tasks"></a>Zadania  
 W poniższej tabeli przedstawiono przykłady dotyczące zadań `My.Settings` obiektu.  
  
|Do|Zobacz|  
|---|---|  
|Ustawienie aplikacji do odczytu|[Porady: odczytywanie ustawień aplikacji w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Zmień ustawienia użytkownika|[Porady: Zmienianie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Utrwalanie ustawień użytkownika|[Porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Tworzenie siatki właściwości dla ustawień użytkownika|[Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyświetlono wartości `Nickname` ustawienie.  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 W tym przykładzie działała, aplikacja musi mieć `Nickname` ustawienia typu `String`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [Porady: odczytywanie ustawień aplikacji w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Porady: Zmienianie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Porady: utrwalanie ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Porady: tworzenie siatek właściwości dla ustawień użytkownika w języku Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
