---
title: 'Porady: tworzenie list wzorzec-szczegół za pomocą formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: aec02e38fbe80302108397543144b1cc9c3ea346
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837146"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: tworzenie list wzorzec-szczegół za pomocą formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Jeśli Twoje <xref:System.Data.DataSet> zawiera serię powiązane tabele, możesz użyć dwóch <xref:System.Windows.Forms.DataGrid> formantów do wyświetlania danych w formacie wzorzec / szczegół. Jeden <xref:System.Windows.Forms.DataGrid> wyznaczony jako główny siatki, a drugi jest wyznaczony jako siatka szczegółów. Po wybraniu wpisu na liście głównej wszystkich wpisów powiązanych podrzędnej liście są wyświetlane szczegółowe informacje. Na przykład jeśli Twoja <xref:System.Data.DataSet> zawiera tabelę Klienci i powiązanej tabeli z zamówieniami, należy określić tabelę Klienci do głównej siatki i na tabeli Orders siatka szczegółów. Po wybraniu odbiorcy z siatki głównej wszystkich zamówień skojarzonych z klientem w tabeli zamówienia będzie wyświetlana w siatce szczegółów.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms Aplikacja**).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>Aby utworzyć listę wzorzec szczegół za pomocą projektanta  
  
1.  Dodaj dwie <xref:System.Windows.Forms.DataGrid> formantów do formularza. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). W programie Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> formantu nie znajduje się w **przybornika** domyślnie. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie elementów do przybornika](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  Poniższe kroki nie mają zastosowania do programu Visual Studio 2005, który używa **źródeł danych** okna dla powiązania danych w czasie projektowania. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) i [porady: wyświetlanie powiązanych danych w aplikacji Windows Forms](https://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
2.  Przeciągnij dwóch lub więcej tabel z **Eksploratora serwera** do formularza.  
  
3.  Z **danych** menu, wybierz opcję **Generowanie zestawu danych**.  
  
4.  Ustaw relacje między tabelami przy użyciu projektanta XML. Aby uzyskać więcej informacji, zobacz "jak: utworzyć jeden do wielu relacji w schematów XML i zestawy danych" w witrynie MSDN.  
  
5.  Zapisz relacje, wybierając **Zapisz wszystko** z **pliku** menu.  
  
6.  Konfigurowanie <xref:System.Windows.Forms.DataGrid> formant, który chcesz wyznaczyć głównego siatki w następujący sposób:  
  
    1.  Wybierz <xref:System.Data.DataSet> z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości.  
  
    2.  Wybieranie tabeli głównej (na przykład "klienci") z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości.  
  
7.  Konfigurowanie <xref:System.Windows.Forms.DataGrid> formant, który chcesz wyznaczyć na siatce szczegółów w następujący sposób:  
  
    1.  Wybierz <xref:System.Data.DataSet> z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości.  
  
    2.  Wybierz relację (na przykład "Customers.CustOrd") między tabelami głównego i szczegółów z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości. Aby można było zobaczyć relację, rozwiń węzeł, klikając znak plus (**+**) logowanie obok tabeli głównej w polu listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Wiązanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
