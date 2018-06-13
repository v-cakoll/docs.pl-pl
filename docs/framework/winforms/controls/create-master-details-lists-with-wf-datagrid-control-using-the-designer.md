---
title: 'Porady: tworzenie list wzorzec-szczegół za pomocą formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 20a6f059efab5469879d3c3a45f4005020414316
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529980"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: tworzenie list wzorzec-szczegół za pomocą formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Jeśli Twoje <xref:System.Data.DataSet> zawiera serię tabel powiązanych, można użyć dwóch <xref:System.Windows.Forms.DataGrid> służy do wyświetlania danych w formacie główny szczegółowy. Jeden <xref:System.Windows.Forms.DataGrid> wyznaczony jako główny siatki, a drugi jest wyznaczony jako siatki szczegółów. Po wybraniu pozycji na liście głównej wszystkie wpisy podrzędnych są wyświetlane na liście szczegóły. Na przykład jeśli Twoje <xref:System.Data.DataSet> zawiera tabelę Klienci i powiązanej tabeli zamówienia, należy określić na tabeli klientów głównym siatki i na tabeli zamówienia siatki szczegółów. Po wybraniu klienta z głównym siatki wszystkich zamówień skojarzonych z klientem w tabeli poleceń będzie wyświetlana w siatce szczegółów.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projektu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>Umożliwia utworzenie listy danych głównych w Projektancie  
  
1.  Dodaj dwa <xref:System.Windows.Forms.DataGrid> formantów w formularzu. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). W [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> formant nie ma na liście **przybornika** domyślnie. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie elementów do przybornika](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  Poniższe kroki nie mają zastosowania do [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], który korzysta z **źródeł danych** okna dla powiązania danych czasu projektowania. Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) i [porady: wyświetlanie powiązanych danych w aplikacji formularzy systemu Windows](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
2.  Przeciągnij co najmniej dwie tabele z **Eksploratora serwera** do formularza.  
  
3.  Z **danych** menu, wybierz opcję **wygenerować zestawu danych**.  
  
4.  Ustaw relacje między tabelami przy użyciu narzędzia Projektant XML. Aby uzyskać więcej informacji, zobacz "jak: utworzyć jeden do wielu relacje w schematów XML i zestawy danych" w witrynie MSDN.  
  
5.  Zapisz relacje wybierając **Zapisz wszystko** z **pliku** menu.  
  
6.  Skonfiguruj <xref:System.Windows.Forms.DataGrid> formant, który chcesz wyznaczyć wzorca siatki w następujący sposób:  
  
    1.  Wybierz <xref:System.Data.DataSet> z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości.  
  
    2.  Wybierz tabelę głównego (na przykład "odbiorcy") z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości.  
  
7.  Skonfiguruj <xref:System.Windows.Forms.DataGrid> formant, który chcesz wyznaczyć siatki szczegółów w następujący sposób:  
  
    1.  Wybierz <xref:System.Data.DataSet> z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości.  
  
    2.  Wybierz relację (na przykład "Customers.CustOrd") pomiędzy tabelami głównego i szczegółów z listy rozwijanej w <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości. Aby zobaczyć relację, rozwiń węzeł, klikając plus (**+**) znakiem obok tabeli głównej w listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [DataGrid, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
