---
title: Powiązywanie danych z kontrolką DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: d49a718e42a989c731cdf748fb63a6305ee096bf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626333"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: powiązywanie danych z formantem DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Za pomocą projektanta można połączyć kontrolę <xref:System.Windows.Forms.DataGridView> ze źródłami danych różnych odmian, w tym bazami danych, obiektami biznesowymi lub usługami sieci Web. Po powiązaniu formantu ze źródłem danych przy użyciu projektanta, formant jest automatycznie powiązany ze składnikiem <xref:System.Windows.Forms.BindingSource>, który reprezentuje źródło danych. Ponadto kolumny są generowane automatycznie w formancie, aby odpowiadały informacje o schemacie dostarczone przez źródło danych.

 Po wygenerowaniu kolumn można je zmodyfikować, aby spełniały Twoje potrzeby. Na przykład można usunąć lub ukryć kolumny, które nie są wyświetlane, można zmienić ich rozmieszczenie lub można zmodyfikować typy kolumn. Aby uzyskać więcej informacji na temat modyfikowania kolumn, zobacz tematy wymienione w sekcji Zobacz też.

 Można również powiązać wiele formantów <xref:System.Windows.Forms.DataGridView> z powiązanymi tabelami, aby utworzyć relacje wzorzec/szczegóły. W tej konfiguracji jedna kontrolka Wyświetla tabelę nadrzędną, a inna kontrolka wyświetla tylko te wiersze z tabeli podrzędnej, które są powiązane z bieżącym wierszem w tabeli nadrzędnej. Aby uzyskać więcej informacji, zobacz [How to: Display powiązane dane w aplikacji Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym kontrolkę <xref:System.Windows.Forms.DataGridView> lub dwie kontrolki dla relacji wzorzec/szczegóły. Aby uzyskać informacje o uruchamianiu takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-bind-the-control-to-a-data-source"></a>Aby powiązać formant ze źródłem danych

1. Kliknij symbol akcji projektanta (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) w prawym górnym rogu kontrolki <xref:System.Windows.Forms.DataGridView>.

2. Kliknij strzałkę listy rozwijanej dla opcji **Wybierz źródło danych** .

3. Jeśli projekt nie ma jeszcze źródła danych, kliknij przycisk **Dodaj źródło danych projektu** i postępuj zgodnie z instrukcjami podanymi przez kreatora.

     Aby uzyskać więcej informacji, zobacz [Kreator konfiguracji źródła danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Nowe źródło danych pojawi się w oknie listy rozwijanej **Wybierz źródło danych** . Jeśli nowe źródło danych zawiera tylko jeden element członkowski, taki jak tabela pojedynczej bazy danych, formant zostanie automatycznie powiązany z tym elementem członkowskim. W przeciwnym razie przejdź do następnego kroku.

4. Rozwiń węzły **inne źródła danych** i **źródła danych projektu** , jeśli nie zostały jeszcze rozwinięte, a następnie wybierz źródło danych, z którym chcesz powiązać formant.

5. Jeśli źródło danych zawiera więcej niż jeden element członkowski, na przykład jeśli utworzono <xref:System.Data.DataSet?displayProperty=nameWithType>, który zawiera wiele tabel, rozwiń źródło danych, a następnie wybierz konkretny element członkowski, z którym ma zostać utworzone powiązanie.

6. Aby utworzyć relację wzorzec/szczegóły, w oknie listy rozwijanej **Wybierz źródło danych** dla drugiej kontrolki <xref:System.Windows.Forms.DataGridView> rozwiń <xref:System.Windows.Forms.BindingSource> utworzone dla tabeli nadrzędnej, a następnie wybierz powiązaną tabelę podrzędną z wyświetlonej listy.

    > [!NOTE]
    > Jeśli projekt ma już źródło danych, możesz również użyć okna **źródła danych** , aby utworzyć formularz danych. Aby uzyskać więcej informacji, zobacz [okno źródła danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Instrukcje: łączenie się z danymi w bazie danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: zmienianie typu kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: ukrywanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](hide-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: określanie kolumn jako tylko do odczytu w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Okno źródeł danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Instrukcje: wyświetlanie powiązanych danych w aplikacji Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
