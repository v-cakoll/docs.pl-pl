---
title: 'Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 7509e2f5035cb05c20af379f9f6a141177d540d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127052"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy systemu Windows
Gdy zachodzi potrzeba wyświetlenia bardzo dużych ilości danych tabelarycznych w <xref:System.Windows.Forms.DataGridView> kontrolki, można ustawić <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość `true` i jawnie zarządzać kontrolki interakcji z jej magazynem danych. Dzięki temu można dostosowywać wydajność kontrolki w tej sytuacji.  
  
 <xref:System.Windows.Forms.DataGridView> Kontrola zapewnia kilka zdarzeń, które może obsłużyć do interakcji z niestandardowego magazynu danych. Ten przewodnik przeprowadzi Cię przez proces implementowania tych programów obsługi zdarzeń. W przykładzie kodu, w tym temacie korzysta z źródła danych bardzo prosty w celach ilustracyjnych. W środowisku produkcyjnym zazwyczaj załaduje tylko tych wierszy, które są potrzebne do wyświetlania w pamięci podręcznej i obsługiwać <xref:System.Windows.Forms.DataGridView> zdarzenia w interakcję i zaktualizuj pamięć podręczną. Aby uzyskać więcej informacji, zobacz [Implementowanie trybu wirtualnego przy użyciu ładowanie danych just in time w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-implement-virtual-mode"></a>Aby zaimplementować trybu wirtualnego  
  
1.  Utwórz klasę, która pochodzi od klasy <xref:System.Windows.Forms.Form> i zawiera <xref:System.Windows.Forms.DataGridView> kontroli.  
  
     Poniższy kod zawiera kilka podstawowych inicjowania. Deklaruje niektóre zmienne, które będą używane w kolejnych krokach, zapewnia `Main` metody i zapewnia prosty formularz układu w konstruktorze klasy.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzeń, która inicjuje <xref:System.Windows.Forms.DataGridView> kontroli i wypełnia magazynu danych z przykładowymi wartościami.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValueNeeded> zdarzeń, który pobiera wartość żądanej komórki z magazynu danych lub `Customer` obiektu aktualnie w trakcie edycji.  
  
     To zdarzenie występuje zawsze, gdy <xref:System.Windows.Forms.DataGridView> kontrolka wymaga malowania komórki.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValuePushed> zdarzeń, która przechowuje wartość edytowane komórki w `Customer` obiekt reprezentujący wiersz edytowany. To zdarzenie występuje, gdy użytkownik zatwierdza zmiany wartości komórki.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.NewRowNeeded> zdarzenia, które tworzy nową `Customer` wiersz nowo utworzony obiekt.  
  
     To zdarzenie występuje, gdy użytkownik wprowadzi wiersza dla nowych rekordów.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowValidated> zdarzeń, która zapisuje nowe lub zmodyfikowane wiersze w magazynie danych.  
  
     To zdarzenie występuje, gdy użytkownik zmienia bieżący wiersz.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> zdarzeń, która wskazuje, czy <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzeń ma miejsce, gdy użytkownik sygnalizuje operacja cofania wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub raz poza trybem edycji.  
  
     Domyślnie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> występuje po wierszu operacja cofania, gdy zmodyfikowano wszystkie komórki w bieżącym wierszu, chyba że <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> właściwość jest ustawiona na `true` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> programu obsługi zdarzeń. To zdarzenie jest przydatne, gdy zakres zatwierdzenia jest określana w czasie wykonywania.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzenia, które odrzuca wszystkie wartości `Customer` obiekt reprezentujący bieżącego wiersza.  
  
     To zdarzenie występuje, gdy użytkownik sygnalizuje operacja cofania wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub raz poza trybem edycji. To zdarzenie nie występuje, jeśli zmodyfikowano żadnych komórek w bieżącym wierszu lub wartość <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> została ustawiona właściwość `false` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> programu obsługi zdarzeń.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.UserDeletingRow> zdarzenia, które usuwa istniejące `Customer` obiektu z magazynu danych lub odrzuca wszystkie niezapisane `Customer` wiersz nowo utworzony obiekt.  
  
     To zdarzenie występuje, gdy użytkownik usuwa wiersz, klikając nagłówek wiersza i naciskając klawisz DELETE.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implementowanie prostego `Customers` klasy do reprezentowania elementów danych używane przez ten przykład kodu.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Skompilować i uruchomić aplikację.  
  
     Zostanie wyświetlony <xref:System.Windows.Forms.DataGridView> kontroli wypełniane przy użyciu trzech rekordów klientów. Można zmodyfikować wartości wielu komórek w wierszu, a następnie naciśnij klawisz ESC, dwa razy w trybie edycji, a po poza trybem edycji, aby przywrócić cały wiersz do ich oryginalnych wartości. Podczas modyfikowania, dodawanie lub usuwanie wierszy w kontrolce `Customer` zmodyfikowane, dodane lub usunięte również obiekty w magazynie danych.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zapewnia podstawową wiedzę na temat zdarzeń musi obsługiwać na implementowanie trybu wirtualnego w <xref:System.Windows.Forms.DataGridView> kontroli. Możesz ulepszyć to podstawowa aplikacja na różne sposoby:  
  
-   Implementowanie magazyn danych, który przechowuje wartości z zewnętrznej bazy danych. Pamięć podręczną należy pobrać i odrzucić wartości zgodnie z potrzebami, tak aby zawierała tylko co jest potrzebne do wyświetlenia podczas korzystania z małą ilością pamięci na komputerze klienckim.  
  
-   Dostosuj wydajność magazynu danych, w zależności od wymagań. Na przykład możesz chcieć kompensacji wolne połączenia sieciowe, a nie ograniczenia ilości pamięci w komputerze klienckim, używając większy rozmiar pamięci podręcznej i minimalizuje liczbę zapytań do bazy danych.  
  
 Aby uzyskać więcej informacji na temat buforowania wartości z zewnętrznej bazy danych, zobacz [jak: Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w Windows formantu DataGridView formularzy](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Instrukcje: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy systemu Windows](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
