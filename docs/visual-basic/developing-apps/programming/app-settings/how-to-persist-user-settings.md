---
title: 'Instrukcje: Utrwalanie ustawień użytkownika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329640"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Porady: utrwalanie ustawień użytkownika w Visual Basic

Możesz użyć metody, `My.Settings.Save` aby zachować zmiany ustawień użytkownika.  
  
 Zazwyczaj aplikacje są przeznaczone do utrwalania zmian ustawień użytkownika po zamknięciu aplikacji. Wynika to z faktu, że zapisywanie ustawień może zająć, w zależności od kilku czynników, kilka sekund.  
  
 Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Chociaż można zmienić i zapisać wartości ustawień zakresu użytkownika w czasie wykonywania, ustawienia zakresu aplikacji są tylko do odczytu i nie można ich programowo zmienić. Ustawienia zakresu aplikacji można zmienić podczas tworzenia aplikacji, za pomocą **projektanta projektu**lub edytując plik konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Przykład  

 Ten przykład zmienia wartość ustawienia `LastChanged` użytkownika i zapisuje tę zmianę przez wywołanie `My.Settings.Save` metody.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Aby ten przykład działał, aplikacja musi mieć ustawienie `LastChanged` użytkownika o typie. `Date` Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Zobacz też

- [My.Settings, obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Porady: odczytywanie ustawień aplikacji w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Porady: zmienianie ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Porady: tworzenie siatek właściwości dla ustawień użytkownika w Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Zarządzanie ustawieniami aplikacji (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
