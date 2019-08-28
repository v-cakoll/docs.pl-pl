---
title: 'Przewodnik: Tworzenie formularza głównego szczegółów przy użyciu dwóch Windows Forms formantów DataGridView'
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
ms.openlocfilehash: 4212c7223aca6a5e7de3189d5f6b2757453cc438
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046098"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Przewodnik: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy systemu Windows

Jednym z najpopularniejszych scenariuszy używania <xref:System.Windows.Forms.DataGridView> kontrolki jest formularz *wzorzec/szczegóły* , w którym wyświetlana jest relacja nadrzędny/podrzędny między dwiema tabelami baz danych. Wybranie wierszy w tabeli głównej powoduje, że tabela szczegółów ma być aktualizowana z odpowiednimi danymi podrzędnymi.

Implementowanie formularza wzorzec/szczegół jest łatwe przy użyciu interakcji między <xref:System.Windows.Forms.DataGridView> formantem <xref:System.Windows.Forms.BindingSource> a składnikiem. W tym instruktażu utworzysz formularz przy użyciu dwóch <xref:System.Windows.Forms.DataGridView> formantów i dwóch <xref:System.Windows.Forms.BindingSource> składników. W formularzu zostaną wyświetlone dwie powiązane tabele w przykładowej bazie danych Northwind SQL Server `Customers` : `Orders`i. Po zakończeniu będziesz mieć formularz, który pokazuje wszystkich klientów w bazie danych Master <xref:System.Windows.Forms.DataGridView> i wszystkie zamówienia dla wybranego klienta w szczegółowym <xref:System.Windows.Forms.DataGridView>zakresie.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Utwórz formularz wzorzec/szczegół za pomocą dwóch Windows Forms formantów](create-a-master-detail-form-using-two-datagridviews.md)DataGridView.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do serwera z przykładową bazą danych Northwind SQL Server.

## <a name="creating-the-form"></a>Tworzenie formularza

#### <a name="to-create-a-masterdetail-form"></a>Aby utworzyć formularz główny/szczegółowy

1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera dwie <xref:System.Windows.Forms.DataGridView> kontrolki i <xref:System.Windows.Forms.BindingSource> dwa składniki. Poniższy kod zawiera podstawowe inicjowanie formularza i zawiera `Main` metodę. Jeśli używasz projektanta programu Visual Studio do utworzenia formularza, możesz użyć kodu wygenerowanego przez projektanta zamiast tego kodu, ale upewnij się, że w tym miejscu użyto nazw przedstawionych w deklaracjach zmiennych.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Zaimplementuj metodę w definicji klasy formularza, aby obsłużyć szczegóły łączenia się z bazą danych. W `GetData` tym przykładzie zastosowano metodę, która wypełnia <xref:System.Data.DataSet> obiekt, dodaje <xref:System.Data.DataRelation> obiekt do zestawu danych i wiąże <xref:System.Windows.Forms.BindingSource> składniki. Pamiętaj, aby ustawić `connectionString` zmienną na wartość odpowiednią dla bazy danych.

    > [!IMPORTANT]
    > Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Zaimplementuj <xref:System.Windows.Forms.Form.Load> procedurę obsługi dla zdarzenia formularza, która wiąże <xref:System.Windows.Forms.DataGridView> kontrolki ze <xref:System.Windows.Forms.BindingSource> składnikami i wywołuje `GetData` metodę. Poniższy przykład zawiera kod, który zmienia rozmiar <xref:System.Windows.Forms.DataGridView> kolumn w celu dopasowania do wyświetlanych danych.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

- Skompiluj i uruchom aplikację.

  Zobaczysz dwie <xref:System.Windows.Forms.DataGridView> kontrolki, jeden nad drugim. Na górze są klientami z tabeli Northwind `Customers` , a u dołu `Orders` są odpowiednie dla wybranego klienta. W miarę zaznaczania innych wierszy w górnej <xref:System.Windows.Forms.DataGridView>części zawartości dolnej <xref:System.Windows.Forms.DataGridView> zmiany odpowiednio.

## <a name="next-steps"></a>Następne kroki

Ta aplikacja zapewnia podstawowe informacje o <xref:System.Windows.Forms.DataGridView> możliwościach formantu. Wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> kontrolki można dostosować na kilka sposobów:

- Zmień style obramowania i nagłówka. Aby uzyskać więcej informacji, zobacz [jak: Zmień style obramowania i linii siatki w kontrolce](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView Windows Forms.

- Włącz lub Ogranicz dane wejściowe użytkownika do <xref:System.Windows.Forms.DataGridView> kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Zapobiegaj dodawaniu i usuwaniu wierszy w kontrolce](prevent-row-addition-and-deletion-datagridview.md)DataGridView Windows Forms i [instrukcje: Ustaw kolumny jako tylko do odczytu w kontrolce](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Sprawdź poprawność danych <xref:System.Windows.Forms.DataGridView> wejściowych użytkownika do kontrolki. Aby uzyskać więcej informacji, [zobacz Przewodnik: Sprawdzanie poprawności danych w kontrolce](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, [zobacz Przewodnik: Implementowanie trybu wirtualnego w kontrolce](implementing-virtual-mode-wf-datagridview-control.md)DataGridView Windows Forms.

- Dostosuj wygląd komórek. Aby uzyskać więcej informacji, zobacz [jak: Dostosuj wygląd komórek w kontrolce](customize-the-appearance-of-cells-in-the-datagrid.md) DataGridView Windows Forms i [instrukcje: Ustaw domyślne style komórek dla kontrolki](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Tworzenie formularza wzorzec/szczegół za pomocą dwóch Windows Forms formantów DataGridView](create-a-master-detail-form-using-two-datagridviews.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
