---
title: 'Wskazówki: Tworzenie formularza głównego-szczegółowego przy użyciu dwóch formantów DataGridView'
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
ms.openlocfilehash: bb3da36430c7493b941f3711cb584b4517d5bd54
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740583"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Wskazówki: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataGridView formularzy systemu Windows

Jednym z najczęstszych scenariuszy używania kontrolki <xref:System.Windows.Forms.DataGridView> jest formularz *wzorzec/szczegóły* , w którym jest wyświetlana relacja nadrzędna/podrzędna między dwiema tabelami baz danych. Wybranie wierszy w tabeli głównej powoduje, że tabela szczegółów ma być aktualizowana z odpowiednimi danymi podrzędnymi.

Implementowanie formularza wzorzec/szczegół jest łatwe przy użyciu interakcji między kontrolką <xref:System.Windows.Forms.DataGridView> a składnikiem <xref:System.Windows.Forms.BindingSource>. W tym instruktażu utworzysz formularz przy użyciu dwóch <xref:System.Windows.Forms.DataGridView> formantów i dwóch składników <xref:System.Windows.Forms.BindingSource>. W formularzu zostaną wyświetlone dwie powiązane tabele w przykładowej bazie danych Northwind SQL Server: `Customers` i `Orders`. Po zakończeniu zostanie wyświetlony formularz pokazujący wszystkich klientów w bazie danych w <xref:System.Windows.Forms.DataGridView> głównym oraz wszystkie zamówienia dla wybranego klienta w <xref:System.Windows.Forms.DataGridView>szczegółowym.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Create a master/detail form przy użyciu dwóch Windows Forms formantów DataGridView](create-a-master-detail-form-using-two-datagridviews.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do serwera z przykładową bazą danych Northwind SQL Server.

## <a name="creating-the-form"></a>Tworzenie formularza

#### <a name="to-create-a-masterdetail-form"></a>Aby utworzyć formularz główny/szczegółowy

1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera dwie kontrolki <xref:System.Windows.Forms.DataGridView> i dwa składniki <xref:System.Windows.Forms.BindingSource>. Poniższy kod zawiera podstawowe inicjowanie formularza i zawiera metodę `Main`. Jeśli używasz projektanta programu Visual Studio do utworzenia formularza, możesz użyć kodu wygenerowanego przez projektanta zamiast tego kodu, ale upewnij się, że w tym miejscu użyto nazw przedstawionych w deklaracjach zmiennych.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Zaimplementuj metodę w definicji klasy formularza, aby obsłużyć szczegóły łączenia się z bazą danych. W tym przykładzie zastosowano metodę `GetData`, która wypełnia obiekt <xref:System.Data.DataSet>, dodaje obiekt <xref:System.Data.DataRelation> do zestawu danych i wiąże składniki <xref:System.Windows.Forms.BindingSource>. Pamiętaj, aby ustawić zmienną `connectionString` na wartość odpowiednią dla bazy danych.

    > [!IMPORTANT]
    > Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.Load> formularza, która wiąże kontrolki <xref:System.Windows.Forms.DataGridView> ze składnikami <xref:System.Windows.Forms.BindingSource> i wywołuje metodę `GetData`. Poniższy przykład zawiera kod, który zmienia rozmiar <xref:System.Windows.Forms.DataGridView> kolumn w celu dopasowania do wyświetlanych danych.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

- Skompiluj i uruchom aplikację.

  Zobaczysz dwie <xref:System.Windows.Forms.DataGridView> kontrolki, jedno nad drugim. Na górze są klientami z tabeli Northwind `Customers`, a u dołu są `Orders` odpowiadające wybranemu klientowi. Po wybraniu różnych wierszy w górnej <xref:System.Windows.Forms.DataGridView>zawartość dolnego <xref:System.Windows.Forms.DataGridView> zostanie odpowiednio zmieniona.

## <a name="next-steps"></a>Następne kroki

Ta aplikacja zapewnia podstawowe informacje o możliwościach kontrolki <xref:System.Windows.Forms.DataGridView>. Wygląd i zachowanie kontrolki <xref:System.Windows.Forms.DataGridView> można dostosować na kilka sposobów:

- Zmień style obramowania i nagłówka. Aby uzyskać więcej informacji, zobacz [How to: zmiana stylu obramowania i linii siatki w kontrolce DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Włącz lub Ogranicz dane wejściowe użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji, zobacz [How to: Zapobieganie dodawaniu i usuwaniu wierszy w kontrolce datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md)i [instrukcje: Określanie kolumn jako tylko do odczytu w kontrolce DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Sprawdź poprawność danych wejściowych użytkownika do kontrolki <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji, zobacz [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Obsługa bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Dostosuj wygląd komórek. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie wyglądu komórek w kontrolce datagridview Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) i [instrukcje: Ustawianie domyślnych stylów komórek dla kontrolki DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms](create-a-master-detail-form-using-two-datagridviews.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
