---
title: 'Porady: powiązywanie danych z formantem DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 1c2b3d9cb9664fccc28ce32889491363807a6560
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485758"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: powiązywanie danych z formantem DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Projektant umożliwia łączenie <xref:System.Windows.Forms.DataGridView> kontrolki źródła danych na kilka różnych odmian, w tym baz danych, obiekty biznesowe lub usług sieci Web. Gdy powiąże formant ze źródłem danych przy użyciu narzędzia Projektant kontrolki zostanie automatycznie powiązany <xref:System.Windows.Forms.BindingSource> składnik, który reprezentuje źródło danych. Ponadto kolumny są automatycznie generowane w formancie do dopasowania informacji o schemacie, dostarczone przez źródło danych.  
  
 Od wygenerowania kolumn, można zmodyfikować je stosownie do potrzeb. Na przykład, usuń lub ukrywanie kolumn nie jest w trakcie wyświetlania, można zmienić kolejność kolumn lub zmodyfikować typy kolumn. Aby uzyskać więcej informacji na temat modyfikowania kolumn zobacz tematy wymienione w sekcji Zobacz też.  
  
 Możesz również powiązać wiele <xref:System.Windows.Forms.DataGridView> kontrolek w tabelach pokrewnych w celu utworzenia relacji wzorzec/szczegół. W tej konfiguracji jeden formant Wyświetla tabelę nadrzędną, a inny formant wyświetli tylko wiersze z tabeli podrzędnej that are related to bieżący wiersz w tabeli nadrzędnej. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie powiązanych danych w aplikacji Windows Forms](https://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą formularza, który zawiera <xref:System.Windows.Forms.DataGridView> dwie kontrolki dla relacji wzorzec/szczegół. Uzyskać informacji o uruchamianiu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>Aby powiązać formant ze źródłem danych  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli.  
  
2.  Kliknij strzałkę listy rozwijanej dla **wybierz źródło danych** opcji.  
  
3.  Jeśli projekt nie ma źródła danych, kliknij przycisk **Dodaj źródło danych projektu** i postępuj zgodnie z instrukcjami, wskazane przez kreatora.  
  
     Aby uzyskać więcej informacji, zobacz [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Nowego źródła danych będą wyświetlane w **wybierz źródło danych** okna listy rozwijanej. Jeśli nowe źródło danych zawiera tylko jednego członka, takiego jak tabela pojedynczej bazy danych, formant będzie automatycznie wiązany tego członka. W przeciwnym razie przejdź do następnego kroku.  
  
4.  Rozwiń **innych źródeł danych** i **zdroje dat projektu** węzłów, jeśli nie są jeszcze rozwinięte, a następnie wybierz źródło danych, aby powiązać formant.  
  
5.  Jeśli źródło danych zawiera więcej niż jeden element członkowski, np. Jeśli utworzono <xref:System.Data.DataSet?displayProperty=nameWithType> zawierający wiele tabel, rozwiń węzeł źródła danych, a następnie wybierz określonego członka, aby powiązać.  
  
6.  Aby tworzenie relacji wzorzec/szczegół w **wybierz źródło danych** okna listy rozwijanej na sekundę <xref:System.Windows.Forms.DataGridView> sterowania, a następnie rozwiń <xref:System.Windows.Forms.BindingSource> utworzone dla tabeli nadrzędnej, a następnie wybierz pokrewnej tabeli podrzędnej na liście wyświetlane.  
  
    > [!NOTE]
    >  Jeśli projekt zawiera już źródło danych, można również użyć **źródeł danych** okna, aby utworzyć formularz danych. Aby uzyskać więcej informacji, zobacz [okna źródeł danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 [Porady: łączenie z danymi w bazie danych](https://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)  
 [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: zmienianie typu kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 [Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: ukrywanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: określanie kolumn jako tylko do odczytu w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 [Porady: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Okno źródeł danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)  
 [Porady: wyświetlanie powiązanych danych w Windows Forms aplikacji](https://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
