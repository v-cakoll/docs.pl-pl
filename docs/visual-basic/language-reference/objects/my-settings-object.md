---
title: My.Settings — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: c905ff85c8e9729dd4d6068f0d34f729962bbb57
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372404"
---
# <a name="mysettings-object"></a>My.Settings — Obiekt
Zawiera właściwości i metody uzyskiwania dostępu do ustawień aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 `My.Settings`Obiekt zapewnia dostęp do ustawień aplikacji i umożliwia dynamiczne przechowywanie i pobieranie ustawień właściwości oraz innych informacji dotyczących aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Właściwości  
 Właściwości `My.Settings` obiektu zapewniają dostęp do ustawień aplikacji. Aby dodać lub usunąć ustawienia, użyj **projektanta ustawień**.  
  
 Każde ustawienie ma **nazwę**, **typ**, **zakres**i **wartość**, a te ustawienia określają, jak Właściwość uzyskiwania dostępu do każdego ustawienia pojawia się w `My.Settings` obiekcie:  
  
- **Nazwa** określa nazwę właściwości.  
  
- **Typ** określa typ właściwości.  
  
- **Zakres** wskazuje, czy właściwość jest tylko do odczytu. Jeśli wartość jest **aplikacją**, właściwość jest tylko do odczytu; Jeśli wartość to **User**, właściwość jest do odczytu i zapisu.  
  
- **Wartość** jest wartością domyślną właściwości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|---|---|  
|`Reload`|Ponownie ładuje ustawienia użytkownika z ostatnich zapisanych wartości.|  
|`Save`|Zapisuje bieżące ustawienia użytkownika.|  
  
 `My.Settings`Obiekt zawiera również zaawansowane właściwości i metody dziedziczone z <xref:System.Configuration.ApplicationSettingsBase> klasy.  
  
## <a name="tasks"></a>Zadania  
 W poniższej tabeli przedstawiono przykłady zadań związanych z `My.Settings` obiektem.  
  
|Do|Zobacz|  
|---|---|  
|Odczytaj ustawienie aplikacji|[Porady: odczytywanie ustawień aplikacji w Visual Basic](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Zmiana ustawienia użytkownika|[Porady: zmienianie ustawień użytkownika w Visual Basic](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Utrwalanie ustawień użytkownika|[Porady: utrwalanie ustawień użytkownika w Visual Basic](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Tworzenie siatki właściwości dla ustawień użytkownika|[Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Przykład  
 Ten przykład wyświetla wartość `Nickname` Ustawienia.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby ten przykład działał, aplikacja musi mieć `Nickname` ustawienie typu `String` .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Configuration.ApplicationSettingsBase>
- [Porady: odczytywanie ustawień aplikacji w Visual Basic](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Porady: zmienianie ustawień użytkownika w Visual Basic](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Porady: utrwalanie ustawień użytkownika w Visual Basic](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
