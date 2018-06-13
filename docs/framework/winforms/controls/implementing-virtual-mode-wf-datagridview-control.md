---
title: 'Wskazówki: implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 52e93ebe0b2903fdf2fe97f4ce812331e740f8b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539922"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Wskazówki: implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows
Jeśli chcesz wyświetlić bardzo dużych ilości danych tabelarycznych w <xref:System.Windows.Forms.DataGridView> sterowania, można ustawić <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości `true` i jawnego zarządzania formantu interakcji z jej magazynem danych. Dzięki temu można dostrojenie wydajności formantu w tej sytuacji.  
  
 <xref:System.Windows.Forms.DataGridView> Kontrola zapewnia kilka zdarzeń, które może obsłużyć do interakcji z niestandardowego magazynu danych. Ten przewodnik ułatwia wdrażanie tych programów obsługi zdarzeń. Przykładowy kod w tym temacie korzysta z źródła danych bardzo proste w celach ilustracyjnych. W środowisku produkcyjnym zwykle załaduje tylko na wierszach, które są potrzebne do wyświetlenia w pamięci podręcznej i obsługi <xref:System.Windows.Forms.DataGridView> zdarzenia do i z aktualizacji pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [Implementowanie trybu wirtualnego przy użyciu just in time w formancie DataGridView formularzy systemu Windows podczas ładowania danych](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-implement-virtual-mode"></a>Aby zaimplementować tryb wirtualny  
  
1.  Utwórz klasę pochodną <xref:System.Windows.Forms.Form> i zawiera <xref:System.Windows.Forms.DataGridView> formantu.  
  
     Poniższy kod zawiera niektóre podstawowe inicjowania. Deklaruje niektóre zmienne, które będą używane w kolejnych krokach, zapewnia `Main` metody i udostępnia układu formularza proste w konstruktorze klasy.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzenie, które inicjuje <xref:System.Windows.Forms.DataGridView> kontroli i wypełnia magazynu danych z wartości przykładowych.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValueNeeded> zdarzeń, który pobiera wartość komórki żądanego z magazynu danych lub `Customer` obiektu obecnie w edycji.  
  
     To zdarzenie występuje zawsze, gdy <xref:System.Windows.Forms.DataGridView> formant wymaga malowania komórki.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CellValuePushed> zdarzeń, która przechowuje wartość edytowanej komórki w `Customer` obiekt reprezentujący wiersz edytowany. To zdarzenie występuje, gdy użytkownik zatwierdza zmiany wartości komórki.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.NewRowNeeded> zdarzenie, które tworzy nową `Customer` obiekt reprezentujący nowo utworzony wiersza.  
  
     To zdarzenie występuje, gdy użytkownik wprowadzi wiersz dla nowych rekordów.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowValidated> zdarzenie, które zapisuje nowych lub zmodyfikowanych wierszy w magazynie danych.  
  
     To zdarzenie występuje, gdy użytkownik zmieni bieżącego wiersza.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> zdarzeń, która wskazuje, czy <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzeń ma miejsce, gdy użytkownik sygnały odwrócenie wiersza, naciskając klawisz ESC dwa razy w trybie edycji lub raz poza trybem edycji.  
  
     Domyślnie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> występuje po odwrócenie wierszy, gdy wszystkie komórki w bieżącym wierszu zostały zmodyfikowane, chyba że <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> właściwość jest ustawiona na `true` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obsługi zdarzeń. To zdarzenie jest przydatne, gdy zakres zatwierdzania jest określana w czasie wykonywania.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.CancelRowEdit> zdarzenie, które odrzuca wszystkie wartości `Customer` obiekt reprezentujący bieżącego wiersza.  
  
     To zdarzenie występuje, gdy użytkownik sygnały odwrócenie wiersza, naciskając klawisz ESC dwa razy w trybie edycji lub raz poza trybem edycji. To zdarzenie nie występuje, jeśli żadna z komórek w bieżącym wierszu zostały zmodyfikowane lub wartość <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> ustawioną właściwość `false` w <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obsługi zdarzeń.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implementowanie obsługi dla <xref:System.Windows.Forms.DataGridView.UserDeletingRow> zdarzenie, które usuwa istniejące `Customer` obiektu z magazynu danych lub odrzuca wszystkie niezapisane `Customer` obiekt reprezentujący nowo utworzony wiersza.  
  
     To zdarzenie występuje, gdy użytkownik usuwa wiersz przez kliknięcie nagłówka wiersza i naciskając klawisz DELETE.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implementowanie prostego `Customers` klasy do reprezentowania elementów danych używany przez ten przykład kodu.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Kompilowanie i uruchamianie aplikacji.  
  
     Zobaczysz <xref:System.Windows.Forms.DataGridView> kontroli wypełniane przy użyciu trzech rekordów klientów. Można zmodyfikować wartości wielu komórek w wierszu, a następnie naciśnij klawisz ESC, dwa razy w trybie edycji i raz poza trybem edycji można przywrócić cały wiersz do jego oryginalnej wartości. Podczas modyfikowania, dodawania i usuwania wierszy w formancie, `Customer` zmodyfikowane, dodane lub usunięte również obiektów w magazynie danych.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera podstawową wiedzę na temat zdarzeń musi obsługiwać do zaimplementowania tryb wirtualny w <xref:System.Windows.Forms.DataGridView> formantu. Można zwiększyć tej aplikacji w warstwie podstawowa na kilka sposobów:  
  
-   Implementuje magazynu danych, który buforuje wartości z zewnętrznej bazy danych. Pamięć podręczna należy pobrać i odrzucić wartości zgodnie z potrzebami, tak aby zawierała tylko niezbędne do wyświetlenia podczas korzystania z małą ilością pamięci na komputerze klienckim.  
  
-   Dostrojenie wydajności magazynu danych, w zależności od wymagań. Na przykład możesz chcieć kompensacji wolne połączenia sieciowe, a nie ograniczenia pamięci komputera klienckiego za pomocą większego rozmiaru pamięci podręcznej i minimalizację liczby zapytań bazy danych.  
  
 Aby uzyskać więcej informacji na temat buforowania wartości z zewnętrznej bazy danych, zobacz [porady: Implementowanie trybu wirtualnego just in time w formancie DataGridView formularzy systemu Windows podczas ładowania danych](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [Instrukcje: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
