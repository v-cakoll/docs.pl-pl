---
title: 'Przewodnik: Tworzenie formularza wzorzec / szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms'
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
ms.openlocfilehash: 774151efb136207a1c4f7a2f8f812bbbaefbf9e1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648211"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Przewodnik: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy systemu Windows
Jedną z najbardziej typowe scenariusze użycia <xref:System.Windows.Forms.DataGridView> formant jest *wzorzec/szczegół* formularza, w którym jest wyświetlana relacji nadrzędny/podrzędny między dwiema tabelami bazy danych. Wybieranie wierszy w tabeli głównej powoduje, że tabela szczegóły aktualizacji za pomocą odpowiednich danych podrzędnych.  
  
 Implementacja formularza wzorzec/szczegół jest łatwe za pomocą interakcji między <xref:System.Windows.Forms.DataGridView> kontroli i <xref:System.Windows.Forms.BindingSource> składnika. W tym instruktażu utworzysz formularza za pomocą dwóch <xref:System.Windows.Forms.DataGridView> kontrolek i dwóch <xref:System.Windows.Forms.BindingSource> składników. Formularz wyświetli dwa powiązane tabele w przykładowej bazie danych Northwind programu SQL Server: `Customers` i `Orders`. Po zakończeniu będziesz mieć formularz, który pokazuje wszystkich klientów w bazie danych w bazie danych master <xref:System.Windows.Forms.DataGridView> i wszystkich zamówień dla zaznaczonego klienta w szczegółach <xref:System.Windows.Forms.DataGridView>.  
  
 Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms](create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
- Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-create-a-masterdetail-form"></a>Aby utworzyć formularza wzorzec/szczegół  
  
1. Utwórz klasę, która pochodzi od klasy <xref:System.Windows.Forms.Form> i zawiera dwa <xref:System.Windows.Forms.DataGridView> kontrolek i dwóch <xref:System.Windows.Forms.BindingSource> składników. Poniższy kod zawiera inicjowanie podstawowej postaci oraz `Main` metody. Tworzenie formularza za pomocą projektanta programu Visual Studio, możesz użyć projektanta wygenerowanego kodu, zamiast tego kodu, ale należy używać nazw wyświetlanych w deklaracjach zmiennych w tym miejscu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2. W definicji klasy formularza do obsługi szczegółowych informacji o połączenie z bazą danych, należy zaimplementować metodę. W tym przykładzie użyto `GetData` metody, która wypełnia <xref:System.Data.DataSet> obiektów, dodaje <xref:System.Data.DataRelation> obiekt do zestawu danych, a następnie tworzy powiązania <xref:System.Windows.Forms.BindingSource> składników. Pamiętaj ustawić `connectionString` zmiennej na wartość, która jest odpowiednia dla bazy danych.  
  
    > [!IMPORTANT]
    >  Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3. Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzeń, która jest powiązywana <xref:System.Windows.Forms.DataGridView> mające na celu <xref:System.Windows.Forms.BindingSource> składników i wywołania `GetData` metody. Poniższy przykład zawiera kod, który zmienia rozmiar <xref:System.Windows.Forms.DataGridView> kolumny, aby dopasować wyświetlanych danych.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
- Skompilować i uruchomić aplikację.  
  
     Zobaczysz dwa <xref:System.Windows.Forms.DataGridView> kontroluje, jeden nad drugim. U góry są klienci z Northwind `Customers` tabeli, a w dolnej części są `Orders` odpowiadający z wybranym klientem. Wybierz różne wiersze w prawym górnym <xref:System.Windows.Forms.DataGridView>, zawartość niższym <xref:System.Windows.Forms.DataGridView> odpowiednio zmienić.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zapewnia podstawową wiedzę na temat <xref:System.Windows.Forms.DataGridView> funkcje formantu. Można dostosować wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> kontroli na kilka sposobów:  
  
- Zmienianie stylów obramowania i nagłówek. Aby uzyskać więcej informacji, zobacz [jak: Zmiana obramowania i formantu DataGridView formularzy style linii siatki w Windows](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Włączać lub ograniczać danych wprowadzonych przez użytkownika <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać więcej informacji, zobacz [jak: Zapobieganie dodawaniu i usuwaniu w Windows formantu DataGridView formularzy](prevent-row-addition-and-deletion-datagridview.md), i [jak: Określanie kolumn jako tylko do odczytu w Windows formantu DataGridView formularzy](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Weryfikowanie danych wejściowych użytkownika do <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać więcej informacji, zobacz [instruktażu: Sprawdzanie poprawności danych w Windows formantu DataGridView formularzy](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
- Obsłużyć bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [instruktażu: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Dostosowywanie wyglądu komórek. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy Windows](customize-the-appearance-of-cells-in-the-datagrid.md) i [jak: Ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy Windows](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms](create-a-master-detail-form-using-two-datagridviews.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
