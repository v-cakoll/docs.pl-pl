---
title: 'Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: aaa26bad5d59f52b4fcba29fd9897aeee5cc9a0f
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303325"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows przy użyciu narzędzia Projektant
Formularze Windows <xref:System.Windows.Forms.ListView> formant może wyświetlić wiele kolumn dla każdej listy elementów w **szczegóły** widoku. Kolumny można użyć, aby wyświetlić kilka rodzajów informacji na temat każdego elementu listy. Na przykład można wyświetlić listę plików, nazwy pliku, typu pliku, rozmiar i Data ostatniej modyfikacji pliku. Aby uzyskać informacje o wprowadzaniu kolumny, gdy są one tworzone, zobacz [jak: Wyświetlanie podelementów w kolumnach za pomocą Windows formantu ListView formularzy](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ListView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-columns-in-the-designer"></a>Aby dodać kolumny w Projektancie  
  
1.  W **właściwości** okna, ustaw dla formantu <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Details>.  
  
2.  W **właściwości** okna, kliknij przycisk **wielokropka** przycisku (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.ListView.Columns%2A> właściwości.  
  
     **ColumnHeader — Edytor kolekcji** pojawia się.  
  
3.  Użyj **Dodaj** przycisk, aby dodać nowe kolumny. Można wybrać nagłówek kolumny i ustawianie jego tekstu (podpis kolumny), wyrównanie tekstu i szerokość.  
  
## <a name="see-also"></a>Zobacz także
- [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie ikon dla kontrolki ListView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
