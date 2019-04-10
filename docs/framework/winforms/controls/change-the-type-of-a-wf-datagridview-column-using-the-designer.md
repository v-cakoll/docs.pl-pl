---
title: 'Instrukcje: zmienianie typu kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: f42bfe9b407e8f81c0eaf5a654d246f7b83567c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208556"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Instrukcje: zmienianie typu kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami można zmienić typ kolumny, który został już dodany do formularzy Windows <xref:System.Windows.Forms.DataGridView> kontroli. Na przykład można modyfikować typy niektórych kolumn, które są generowane automatycznie, gdy powiąże formant ze źródłem danych. Jest to przydatne, gdy tabelę, którą możesz wyświetlić ma kolumn zawierających klucze obce do wierszy w powiązanej tabeli. W takim przypadku można zastąpić tekst kolumny pole zawierające te klucze obce kolumny pola kombi, zawierające bardziej zrozumiały wartości z tabeli powiązanej.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Aby zmienić typ kolumny przy użyciu narzędzia Projektant  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumnę z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, ustaw `ColumnType` właściwości nowego typu kolumny.  
  
    > [!NOTE]
    >  `ColumnType` Właściwości jest właściwością projektowania — tylko od czasu, która określa klasy reprezentujące typ kolumny. Nie jest właściwością rzeczywiste zdefiniowanej w klasie kolumny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy systemu Windows](how-to-add-controls-to-windows-forms.md)
