---
title: 'Instrukcje: Nadawanie kolumnom w trybie tylko do odczytu w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: f2f95982b5b92a47bcc9960942289eae68c20f14
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332406"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: Nadawanie kolumnom w trybie tylko do odczytu w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant
Domyślnie użytkownicy mogą modyfikować tekstu i danych liczbowych są wyświetlane w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontroli. Jeśli chcesz wyświetlić dane, która nie jest przeznaczona do modyfikacji, należy kolumn, które zawierają dane tylko do odczytu. Aby dowiedzieć się, jak sprawić, że formant całkowicie tylko do odczytu, zobacz [jak: Zapobieganie dodawaniu i usuwaniu rzędów Windows do formantu DataGridView przy użyciu narzędzia Projektant formularzy](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a>Aby kolumnę tylko do odczytu przy użyciu narzędzia Projektant  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumnę z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwość `true`.  
  
    > [!NOTE]
    >  Można również ustawić kolumną tylko do odczytu po dodaniu, wybierając **tylko do odczytu** pole wyboru w **Dodaj kolumnę** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Instrukcje: Dodawanie i usuwanie kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Zapobiegaj wierszy i usuwanie w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
