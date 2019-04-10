---
title: 'Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 80ede9b7bc5bf667e03dc0a745fbc0b5f6c2663a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343288"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Formularze Windows <xref:System.Windows.Forms.DataGridView> kontroli musi zawierać kolumny, aby wyświetlić dane. Jeśli użytkownik chce ręcznie wypełnić kontrolki, należy dodać kolumny samodzielnie. Alternatywnie można powiązać formant ze źródłem danych, która generuje i automatycznie wypełnia kolumny. Jeśli źródło danych zawiera więcej kolumn niż mają być wyświetlane, można usunąć zbędne kolumny.  
  
 Poniższe procedury wymagają **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-column-using-the-designer"></a>Aby dodać kolumnę przy użyciu narzędzia Projektant  
  
1. Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Dodaj kolumnę**.  
  
2. W **Dodaj kolumnę** okna dialogowego wybierz **kolumnę z danymi** opcję i wybierz kolumny ze źródła danych lub wybierz **niepowiązanych kolumn** opcji, a kolumna jest definiowana przy użyciu odpowiednich polach.  
  
3. Kliknij przycisk **Dodaj** przycisk, aby dodać kolumnę, co powoduje pojawiają się w projektancie, jeśli istniejące kolumny już nie wypełnia obszaru wyświetlania kontrolki.  
  
    > [!NOTE]
    >  Można zmodyfikować właściwości kolumny w **Edytowanie kolumn** okno dialogowe, które można wywołać z tagu kontrolki.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Aby usunąć kolumnę przy użyciu narzędzia Projektant  
  
1. Wybierz **Edytowanie kolumn** z tagu kontrolki.  
  
2. Wybierz kolumnę z **wybrane kolumny** listy.  
  
3. Kliknij przycisk **Usuń** przycisk, aby usunąć kolumny, które wymusi są usuwane z projektanta.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy systemu Windows](how-to-add-controls-to-windows-forms.md)
