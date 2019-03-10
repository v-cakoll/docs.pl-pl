---
title: 'Instrukcje: Dziedziczenie formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 97964f64f1a846327b2d014088c22e53d85231e4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720868"
---
# <a name="how-to-inherit-windows-forms"></a>Instrukcje: Dziedziczenie formularzy Windows
Tworzenie nowych formularzy Windows przez dziedziczenie z formularzy podstawowy jest wygodny sposób zduplikowane starań bez przechodzenia przez proces całkowicie ponownego tworzenia formularza, za każdym razem, gdy jej potrzebujesz.  
  
 Aby uzyskać więcej informacji na temat dziedziczenie formularzy przy użyciu czasu projektowania **selektor dziedziczenia** okno dialogowe i jak wizualnie rozróżnienie między poziomy zabezpieczeń dziedziczone formantów, zobacz [jak: Dziedziczenie formularzy przy użyciu okna dialogowego selektora dziedziczenia](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Uwaga** celu dziedziczą z formularza, pliku lub przestrzeni nazw, zawierające ten formularz musi zostały skompilowane do pliku wykonywalnego lub biblioteki DLL. Aby skompilować projekt, wybierz opcję **kompilacji** z **kompilacji** menu. Ponadto należy można dodać odwołania do przestrzeni nazw do klasy dziedziczące formularza. Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-inherit-a-form-programmatically"></a>Programowe dziedziczyć formularza  
  
1.  W klasie Dodaj odwołanie do przestrzeni nazw zawierający formularz, który chcesz dziedziczyć.  
  
2.  W definicji klasy Dodaj odwołanie do formularza, aby dziedziczyć. Odwołania powinny zawierać przestrzeń nazw zawierająca formularz, następuje kropka, a następnie nazwa podstawowa samego formularza.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 Gdy dziedziczenie formularzy, należy pamiętać o tym, jakie problemy mogą się pojawić w odniesieniu do programów obsługi zdarzeń, wywoływana dwa razy, ponieważ każde zdarzenie jest obsługiwane zarówno przez klasę bazową i odziedziczoną klasę. Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Rozwiązywanie problemów z dziedziczone procedury obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="see-also"></a>Zobacz także
- [Inherits, instrukcja](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [using](~/docs/csharp/language-reference/keywords/using.md)
- [Efekty modyfikowania wyglądu formularza podstawowego](effects-of-modifying-base-form-appearance.md)
- [Formularze Windows Forms — dziedziczenie wizualizacji](windows-forms-visual-inheritance.md)
