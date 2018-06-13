---
title: 'Wskazówki: Tworzenie formularza wzorzec szczegół za pomocą dwóch formantów DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 38f7c6197fb3ee79119e41ab9620bc3aa2b21900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529444"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Wskazówki: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataGridView formularzy systemu Windows
Jedną z najbardziej typowych scenariuszy stosowania <xref:System.Windows.Forms.DataGridView> formant jest *wzorzec/szczegół* formularza, w którym jest wyświetlany relacji nadrzędny/podrzędny między dwiema tabelami bazy danych. Wybierania wierszy w tabeli głównej powoduje, że tabela szczegółów aktualizowania przy użyciu odpowiednich danych podrzędnych.  
  
 Implementacja formularza wzorzec/szczegół jest łatwy w użyciu interakcji między <xref:System.Windows.Forms.DataGridView> kontroli i <xref:System.Windows.Forms.BindingSource> składnika. W tym przykładzie utworzysz formularza za pomocą dwóch <xref:System.Windows.Forms.DataGridView> kontrolek i dwa <xref:System.Windows.Forms.BindingSource> składników. W formularzu będą wyświetlone dwa powiązane tabele w przykładowej bazie danych Northwind programu SQL Server: `Customers` i `Orders`. Gdy skończysz, konieczne będzie formularz, który zawiera wszystkich klientów z bazy danych we wzorcu <xref:System.Windows.Forms.DataGridView> i wszystkich zleceń dla wybranego klienta w szczegółach <xref:System.Windows.Forms.DataGridView>.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: tworzenie wzorzec/szczegół formularza za pomocą dwóch formantów formularzy systemu Windows DataGridView](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-create-a-masterdetail-form"></a>Aby utworzyć formularz główny/szczegółowy  
  
1.  Utwórz klasę pochodną <xref:System.Windows.Forms.Form> i zawiera dwa <xref:System.Windows.Forms.DataGridView> kontrolek i dwa <xref:System.Windows.Forms.BindingSource> składników. Poniższy kod zawiera podstawowe formularza inicjowania oraz `Main` metody. Tworzenie formularza za pomocą projektanta programu Visual Studio można używać Projektanta wygenerowanego kodu zamiast tego kodu, ale należy użyć nazw wyświetlanych w deklaracjach zmiennych w tym miejscu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  W definicji klasy formularza obsługi szczegóły połączenia z bazą danych, należy zaimplementować metodę. W tym przykładzie użyto `GetData` metodę, która wypełnia <xref:System.Data.DataSet> obiektu powoduje dodanie <xref:System.Data.DataRelation> obiekt do zestawu danych i wiązania <xref:System.Windows.Forms.BindingSource> składników. Należy ustawić `connectionString` zmiennej na wartość, która jest odpowiednia dla Twojej bazy danych.  
  
    > [!IMPORTANT]
    >  Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzeń, która jest powiązywana <xref:System.Windows.Forms.DataGridView> formanty <xref:System.Windows.Forms.BindingSource> składniki i wywołania `GetData` — metoda. Poniższy przykład zawiera kod, który zmienia rozmiar <xref:System.Windows.Forms.DataGridView> kolumn wyświetlanych danych.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Kompilowanie i uruchamianie aplikacji.  
  
     Zobaczysz dwa <xref:System.Windows.Forms.DataGridView> określa jeden nad drugim. U góry są klientów z Northwind `Customers` tabeli i u dołu są `Orders` odpowiadającego danego odbiorcy. Po wybraniu różne wiersze w prawym górnym <xref:System.Windows.Forms.DataGridView>, zawartość niższa <xref:System.Windows.Forms.DataGridView> odpowiednio zmienić.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera podstawowe <xref:System.Windows.Forms.DataGridView> funkcje formantu. Można dostosować wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> sterowania na kilka sposobów:  
  
-   Zmienianie stylów obramowania i nagłówek. Aby uzyskać więcej informacji, zobacz [porady: Zmiana obramowania i style linii siatki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Włącz lub ograniczanie danych wejściowych użytkownika na <xref:System.Windows.Forms.DataGridView> formantu. Aby uzyskać więcej informacji, zobacz [porady: Zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), i [jak: utworzyć tylko do odczytu w kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Sprawdzanie poprawności danych wejściowych użytkownika na <xref:System.Windows.Forms.DataGridView> formantu. Aby uzyskać więcej informacji, zobacz [wskazówki: Sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Obsłużyć bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Dostosowywanie wyglądu komórek. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) i [porady: Ustaw domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)
