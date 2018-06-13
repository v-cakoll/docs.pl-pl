---
title: 'Porady: dziedziczenie formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: ce938d922560c96b5ce3c76756d409af5858492d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522905"
---
# <a name="how-to-inherit-windows-forms"></a>Porady: dziedziczenie formularzy systemu Windows
Tworzenie nowych formularzy systemu Windows przez dziedziczenie z formularzy podstawowy jest to wygodna metoda mają zostać zduplikowane starań bez pośrednictwa całkowicie odtworzenie formularza za każdym razem, gdy wymagają tego procesu.  
  
 Aby uzyskać więcej informacji na temat dziedziczenie formularzy przy użyciu czasu projektowania **selektora dziedziczenia** okno dialogowe i jak wizualnie rozróżnienia poziomów zabezpieczeń dziedziczone formantów, zobacz [porady: dziedziczenie formularzy przy użyciu Okno dialogowe selektora dziedziczenia](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Uwaga** aby dziedziczyć z formularza, pliku lub przestrzeni nazw zawierającej formularza musi skompilowano do pliku wykonywalnego lub DLL. Aby utworzyć projekt, wybierz **kompilacji** z **kompilacji** menu. Ponadto odwołanie do przestrzeni nazw musi można dodać do klasy dziedziczy formularza. Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-inherit-a-form-programmatically"></a>Aby programowo dziedziczą formularza  
  
1.  W klasie Dodaj odwołanie do przestrzeni nazw zawierający formularz, który chcesz dziedziczyć.  
  
2.  W definicji klasy Dodaj odwołanie do formularza, aby dziedziczyć. Odwołania powinny zawierać nazw, zawierający formularz, a następnie okres, a następnie nazwę samego formularza podstawowego.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 Przy dziedziczenie formularzy, należy pamiętać o tym, jakie problemy mogą się pojawić w odniesieniu do obsługi zdarzeń wywoływana dwukrotnie, ponieważ każde zdarzenie jest obsługiwane przez klasę podstawową i dziedziczonej klasie. Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Rozwiązywanie problemów z dziedziczone programów obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Inherits, instrukcja](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Efekty modyfikowania wyglądu formularza podstawowego](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Formularze Windows Forms — dziedziczenie wizualizacji](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
