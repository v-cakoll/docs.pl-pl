---
title: "Porady: formatowanie formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da36f4f79d0016249dead686f305e1b93defceda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: formatowanie formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Stosowanie różnych kolorów do różnych części <xref:System.Windows.Forms.DataGrid> formant może pomóc udostępnia informacje w nim łatwiej odczytywać i interpretowania. Kolor można zastosować do wierszy i kolumn. Wiersze i kolumny można również ukryte lub pokazane według uznania.  
  
 Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> sterowania:  
  
-   Można ustawić właściwości, aby ustanowić domyślny styl wyświetlania danych.  
  
-   Z tego elementu bazowego można dostosować sposób wyświetlania określonych tabel w czasie wykonywania.  
  
-   Na koniec można zmodyfikować kolumny, które są wyświetlane w siatce danych, a także kolory i inne formatowania, który jest wyświetlany.  
  
 Na etapie wstępnym w formatowaniu siatkę danych, można ustawić właściwości <xref:System.Windows.Forms.DataGrid> samej siebie. Te opcje kolor i format tworzą podstawowy, z którego można następnie wprowadzić zmiany w zależności od danych tabele i kolumny wyświetlane.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGrid> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). W [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> formant nie ma na liście **przybornika** domyślnie. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie elementów do przybornika](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Aby ustanowić domyślny styl formantu DataGrid  
  
1.  Wybierz <xref:System.Windows.Forms.DataGrid> formantu.  
  
2.  W **właściwości** okna, ustaw następujące właściwości, zależnie od potrzeb.  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` Właściwość określa kolor wierszach parzystych siatki. Podczas ustawiania <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwość inny kolor, każdego wiersza jest ustawiona na nowy kolor (wiersze, 1, 3, 5 i tak dalej).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kolor tła wierszy parzystych siatki (wiersze, 0, 2, 4, 6 itd.).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Podczas gdy <xref:System.Windows.Forms.DataGrid.BackColor%2A> i <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości określa kolor wierszy w siatce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> właściwość określa kolor obszaru poza obszar wiersza, który jest widoczna tylko siatki jest przewijane w dół lub tylko kilka wierszy zawarte w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl obramowania siatki, jeden z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kolor tła tytuł okna siatki, które pojawia się powyżej siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Czcionka podpisu w górnej części siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kolor tła tytuł okna siatki.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Czcionka używana do wyświetlania tekstu w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Kolor czcionki wyświetlanego przez dane w wiersze siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Kolor linii siatki w siatce danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl linii oddzielających komórki siatki, jeden z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Kolor tła nagłówków wierszy i kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Czcionka używana dla nagłówków kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kolor pierwszego planu nagłówków kolumn siatki, w tym tekst nagłówka kolumny znak plus (+) i znak minus (-) symboli, które rozwijanie i zwijanie wierszy, gdy wielu powiązanych tabel są wyświetlane.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Kolor tekstu wszystkich łączy w siatce danych oraz łącza do tabele podrzędne, Nazwa relacji i tak dalej.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnego za pomocą klasy <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Domyślna szerokość (w pikselach) kolumn w siatce. Ta właściwość jest ustawiana przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwości na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Wysokość wiersza (w pikselach) wierszy w siatce. Ta właściwość jest ustawiana przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwości na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Szerokość nagłówków wiersza siatki.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor tła.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor pierwszego planu.|  
  
    > [!NOTE]
    >  Podczas dostosowywania kolory formantów jest możliwe formantu niedostępny z powodu słabej kolory do wyboru (na przykład czerwony i zielony). Użyj kolorów, które są dostępne na **kolorów systemu** palety, aby uniknąć tego problemu.  
  
     Poniższa procedura wymaga <xref:System.Windows.Forms.DataGrid> formant powiązany z tabelą danych. Aby uzyskać więcej informacji, zobacz [porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Aby ustawić styl tabel i kolumn w tabeli danych w czasie projektowania  
  
1.  Wybierz <xref:System.Windows.Forms.DataGrid> kontrolkę w formularzu.  
  
2.  W **właściwości** wybierz <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości i kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) przycisku.  
  
3.  W **edytora kolekcji Element DataGridTableStyle** okno dialogowe, kliknij przycisk **Dodaj** do dodania do kolekcji styl tabeli.  
  
     Z **edytora kolekcji Element DataGridTableStyle**, można dodawać i Usuń style tabeli, wyświetlania zestawu i właściwości układu oraz zestaw mapowanie nazwy stylów tabeli.  
  
4.  Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość na nazwę mapowania każdy styl tabeli.  
  
     Nazwa mapowania jest używana do określenia, który styl tabeli powinien być używany z tabeli.  
  
5.  W **edytora kolekcji Element DataGridTableStyle**, wybierz pozycję <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości i kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton ")).  
  
6.  W **edytora kolekcji DataGridColumnStyle** okno dialogowe Dodaj style kolumn na styl tabeli został utworzony.  
  
     Z **edytora kolekcji DataGridColumnStyle**, można dodać i usunąć style kolumn, ustawiać właściwości wyświetlania i układu i ustaw nazwę mapowania i ciągi formatowania danych kolumny.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji o ciągach formatowania, zobacz [typy formatowania](../../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Porady: usuwanie lub ukrywanie kolumn w oknach formantu DataGrid formularzy](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid — formant](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
