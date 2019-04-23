---
title: 'Instrukcje: wiązanie danych z kontrolką DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 59a025535e850cf3c773a2a078511d41058bb24c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321851"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: wiązanie danych z kontrolką DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Projektant umożliwia łączenie <xref:System.Windows.Forms.DataGridView> kontrolki źródła danych na kilka różnych odmian, w tym baz danych, obiekty biznesowe lub usług sieci Web. Gdy powiąże formant ze źródłem danych przy użyciu narzędzia Projektant kontrolki zostanie automatycznie powiązany <xref:System.Windows.Forms.BindingSource> składnik, który reprezentuje źródło danych. Ponadto kolumny są automatycznie generowane w formancie do dopasowania informacji o schemacie, dostarczone przez źródło danych.  
  
 Od wygenerowania kolumn, można zmodyfikować je stosownie do potrzeb. Na przykład, usuń lub ukrywanie kolumn nie jest w trakcie wyświetlania, można zmienić kolejność kolumn lub zmodyfikować typy kolumn. Aby uzyskać więcej informacji na temat modyfikowania kolumn zobacz tematy wymienione w sekcji Zobacz też.  
  
 Możesz również powiązać wiele <xref:System.Windows.Forms.DataGridView> kontrolek w tabelach pokrewnych w celu utworzenia relacji wzorzec/szczegół. W tej konfiguracji jeden formant Wyświetla tabelę nadrzędną, a inny formant wyświetli tylko wiersze z tabeli podrzędnej that are related to bieżący wiersz w tabeli nadrzędnej. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie powiązanych danych w Windows Forms aplikacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą formularza, który zawiera <xref:System.Windows.Forms.DataGridView> dwie kontrolki dla relacji wzorzec/szczegół. Aby uzyskać informacji o uruchamianiu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>Aby powiązać formant ze źródłem danych  
  
1. Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli.  
  
2. Kliknij strzałkę listy rozwijanej dla **wybierz źródło danych** opcji.  
  
3. Jeśli projekt nie ma źródła danych, kliknij przycisk **Dodaj źródło danych projektu** i postępuj zgodnie z instrukcjami, wskazane przez kreatora.  
  
     Aby uzyskać więcej informacji, zobacz [Kreatora konfiguracji źródła danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Nowego źródła danych będą wyświetlane w **wybierz źródło danych** okna listy rozwijanej. Jeśli nowe źródło danych zawiera tylko jednego członka, takiego jak tabela pojedynczej bazy danych, formant będzie automatycznie wiązany tego członka. W przeciwnym razie przejdź do następnego kroku.  
  
4. Rozwiń **innych źródeł danych** i **zdroje dat projektu** węzłów, jeśli nie są jeszcze rozwinięte, a następnie wybierz źródło danych, aby powiązać formant.  
  
5. Jeśli źródło danych zawiera więcej niż jeden element członkowski, np. Jeśli utworzono <xref:System.Data.DataSet?displayProperty=nameWithType> zawierający wiele tabel, rozwiń węzeł źródła danych, a następnie wybierz określonego członka, aby powiązać.  
  
6. Aby tworzenie relacji wzorzec/szczegół w **wybierz źródło danych** okna listy rozwijanej na sekundę <xref:System.Windows.Forms.DataGridView> sterowania, a następnie rozwiń <xref:System.Windows.Forms.BindingSource> utworzone dla tabeli nadrzędnej, a następnie wybierz pokrewnej tabeli podrzędnej na liście wyświetlane.  
  
    > [!NOTE]
    >  Jeśli projekt zawiera już źródło danych, można również użyć **źródeł danych** okna, aby utworzyć formularz danych. Aby uzyskać więcej informacji, zobacz [okna źródeł danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Instrukcje: Łączenie z danymi w bazie danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Instrukcje: Dodawanie i usuwanie kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Zmienianie kolejności kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Zmień typ kolumny formantu DataGridView formularzy Windows przy użyciu narzędzia Projektant](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Instrukcje: Blokowanie kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Ukrywanie kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](hide-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Nadawanie kolumnom w trybie tylko do odczytu w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Okno źródeł danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Instrukcje: Wyświetlanie powiązanych danych w aplikacji Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
