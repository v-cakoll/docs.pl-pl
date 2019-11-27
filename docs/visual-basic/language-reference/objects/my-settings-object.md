---
title: My.Settings — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350359"
---
# <a name="mysettings-object"></a>My.Settings — Obiekt
Udostępnia właściwości i metody dostępu do ustawień aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `My.Settings` zapewnia dostęp do ustawień aplikacji i umożliwia dynamiczne przechowywanie i pobieranie ustawień właściwości oraz innych informacji dotyczących aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Właściwości  
 Właściwości obiektu `My.Settings` zapewniają dostęp do ustawień aplikacji. Aby dodać lub usunąć ustawienia, użyj **projektanta ustawień**.  
  
 Każde ustawienie ma **nazwę**, **typ**, **zakres**i **wartość**, a te ustawienia określają, jak Właściwość uzyskiwania dostępu do każdego ustawienia pojawia się w obiekcie `My.Settings`:  
  
- **Nazwa** określa nazwę właściwości.  
  
- **Typ** określa typ właściwości.  
  
- **Zakres** wskazuje, czy właściwość jest tylko do odczytu. Jeśli wartość jest **aplikacją**, właściwość jest tylko do odczytu; Jeśli wartość to **User**, właściwość jest do odczytu i zapisu.  
  
- **Wartość** jest wartością domyślną właściwości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|---|---|  
|`Reload`|Ponownie ładuje ustawienia użytkownika z ostatnio zapisanymi wartościami.|  
|`Save`|Zapisuje bieżące ustawienia użytkownika.|  
  
 Obiekt `My.Settings` udostępnia także zaawansowane właściwości i metody dziedziczone z klasy <xref:System.Configuration.ApplicationSettingsBase>.  
  
## <a name="tasks"></a>Zadania  
 W poniższej tabeli przedstawiono przykłady zadań związanych z obiektem `My.Settings`.  
  
|Do|Zobacz|  
|---|---|  
|Odczyt ustawienia aplikacji|[Instrukcje: odczytywanie ustawień aplikacji w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Zmiana ustawienia użytkownika|[Instrukcje: Zmienianie ustawień użytkownika w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Utrwalanie ustawień użytkownika|[Instrukcje: utrwalanie ustawień użytkownika w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Tworzenie siatki właściwości dla ustawień użytkownika|[Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Przykład  
 Ten przykład wyświetla wartość ustawienia `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby ten przykład działał, aplikacja musi mieć ustawienie `Nickname` typu `String`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.ApplicationSettingsBase>
- [Instrukcje: odczytywanie ustawień aplikacji w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Instrukcje: Zmienianie ustawień użytkownika w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Instrukcje: utrwalanie ustawień użytkownika w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Instrukcje: Tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
