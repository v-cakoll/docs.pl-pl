---
title: 'Przewodnik: implementowanie trybu wirtualnego w formancie DataGridView'
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
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746520"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Wskazówki: implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows
Aby wyświetlić bardzo duże ilości danych tabelarycznych w kontrolce <xref:System.Windows.Forms.DataGridView>, można ustawić właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> na `true` i jawnie zarządzać interakcją formantu z jego magazynem danych. Pozwala to dostosować wydajność kontroli w tej sytuacji.  
  
 Kontrolka <xref:System.Windows.Forms.DataGridView> zawiera kilka zdarzeń, które można obsłużyć w celu współpracy z niestandardowym magazynem danych. Ten przewodnik przeprowadzi Cię przez proces wdrażania tych programów obsługi zdarzeń. Przykład kodu w tym temacie używa bardzo prostego źródła danych na potrzeby ilustracji. W ustawieniu produkcji zwykle ładowane są tylko te wiersze, które mają być wyświetlane w pamięci podręcznej, i obsługują zdarzenia <xref:System.Windows.Forms.DataGridView>, aby współtworzyć i zaktualizować pamięć podręczną. Aby uzyskać więcej informacji, zobacz [implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [jak: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-implement-virtual-mode"></a>Aby zaimplementować tryb wirtualny  
  
1. Utwórz klasę, która dziedziczy z <xref:System.Windows.Forms.Form> i zawiera kontrolkę <xref:System.Windows.Forms.DataGridView>.  
  
     Poniższy kod zawiera pewne inicjalizacje podstawowe. Deklaruje pewne zmienne, które będą używane w kolejnych krokach, zapewnia metodę `Main` i udostępnia prosty układ formularza w konstruktorze klas.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.Load> formularza, która inicjuje formant <xref:System.Windows.Forms.DataGridView> i wypełnia magazyn danych wartościami przykładowymi.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellValueNeeded>, które pobiera żądaną wartość komórki z magazynu danych lub obiektu `Customer`, który jest obecnie w trakcie edycji.  
  
     To zdarzenie występuje, gdy kontrolka <xref:System.Windows.Forms.DataGridView> musi malować komórkę.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellValuePushed>, które przechowuje edytowaną wartość komórki w obiekcie `Customer` reprezentującym edytowany wiersz. To zdarzenie występuje zawsze, gdy użytkownik zatwierdzi zmianę wartości komórki.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.NewRowNeeded>, które tworzy nowy obiekt `Customer` reprezentujący nowo utworzony wiersz.  
  
     To zdarzenie występuje zawsze, gdy użytkownik wprowadzi wiersz dla nowych rekordów.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.RowValidated>, które zapisuje nowe lub zmodyfikowane wiersze w magazynie danych.  
  
     To zdarzenie występuje zawsze, gdy użytkownik zmieni bieżący wiersz.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>, która wskazuje, czy zdarzenie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> nastąpi, gdy użytkownik sygnalizuje ponownie wersję wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub poza trybem edycji.  
  
     Domyślnie <xref:System.Windows.Forms.DataGridView.CancelRowEdit> występuje po zmianie wersji wiersza, gdy wszystkie komórki w bieżącym wierszu zostały zmodyfikowane, chyba że właściwość <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> jest ustawiona na `true` w programie obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>. To zdarzenie jest przydatne, gdy zakres zatwierdzania jest określany w czasie wykonywania.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CancelRowEdit>, które odrzuca wartości obiektu `Customer` reprezentującego bieżący wiersz.  
  
     To zdarzenie występuje, gdy użytkownik sygnalizuje przewinięcie wiersza przez naciśnięcie klawisza ESC dwa razy w trybie edycji lub poza trybem edycji. To zdarzenie nie występuje, jeśli żadna komórka w bieżącym wierszu nie została zmodyfikowana lub jeśli wartość właściwości <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> została ustawiona na `false` w obsłudze zdarzeń <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.UserDeletingRow>, które usuwa istniejący obiekt `Customer` z magazynu danych lub odrzuca niezapisany obiekt `Customer` reprezentujący nowo utworzony wiersz.  
  
     To zdarzenie występuje zawsze, gdy użytkownik usuwa wiersz, klikając nagłówek wiersza i naciskając klawisz DELETE.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Zaimplementuj prostą klasę `Customers`, aby reprezentować elementy danych używane przez ten przykład kodu.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
- Skompiluj i uruchom aplikację.  
  
     Zostanie wyświetlona kontrolka <xref:System.Windows.Forms.DataGridView> zawierająca trzy rekordy klientów. Możesz zmodyfikować wartości wielu komórek w wierszu i nacisnąć klawisz ESC dwa razy w trybie edycji i poza trybem edycji, aby przywrócić pierwotne wartości w całym wierszu. W przypadku modyfikowania, dodawania lub usuwania wierszy w kontrolce `Customer` obiektów w magazynie danych są również modyfikowane, dodawane lub usuwane.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera podstawowe informacje o zdarzeniach, które należy obsłużyć w celu zaimplementowania trybu wirtualnego w kontrolce <xref:System.Windows.Forms.DataGridView>. Tę podstawową aplikację można ulepszyć na wiele sposobów:  
  
- Zaimplementuj magazyn danych, który buforuje wartości z zewnętrznej bazy danych. Pamięć podręczna powinna pobierać i odrzucać wartości zgodnie z potrzebami, tak aby zawierała tylko te dane, które są niezbędne do wyświetlania podczas zużywania niewielkiej ilości pamięci na komputerze klienckim.  
  
- Dostosuj wydajność magazynu danych w zależności od wymagań. Można na przykład zrekompensować wolne połączenia sieciowe zamiast ograniczeń pamięci klienta, używając większego rozmiaru pamięci podręcznej i minimalizując liczbę zapytań bazy danych.  
  
 Aby uzyskać więcej informacji na temat buforowania wartości z zewnętrznej bazy danych, zobacz [How to: Implementuj tryb wirtualny przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
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
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Instrukcje: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
