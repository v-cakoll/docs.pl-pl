---
title: 'Porady: zapewnienie pozostawania wybranego wiersza w tabeli potomnej w prawidłowym położeniu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30929c6163a279bc0ea47d1262f54ec5ff75a87c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a>Porady: zapewnienie pozostawania wybranego wiersza w tabeli potomnej w prawidłowym położeniu
Często po współpracujesz powiązanie danych w formularzach systemu Windows, co jest nazywane nadrzędny/podrzędny lub głównych/szczegółów widoku będą wyświetlane dane. Odnosi się do scenariusz wiązania danych, których dane z tego samego źródła są wyświetlane w dwóch formantów. Zmiana wyboru w jeden formant powoduje danych wyświetlanych w formancie drugi do zmiany. Na przykład pierwszy formant może zawierać listę klientów, a drugi listę zleceń związane z wybranego klienta w pierwszego formantu.  
  
 .NET Framework w wersji 2.0, począwszy od podczas wyświetlania danych w widoku nadrzędny/podrzędny, że trzeba będzie wykonać dodatkowe czynności, aby upewnić się, czy obecnie wybrany wiersz w tabeli podrzędnej nie zostanie zresetowana do pierwszego wiersza tabeli. W tym celu należy do pamięci podręcznej położenie elementów podrzędnych tabeli i resetuje je po zmianie tabeli nadrzędnej. Zazwyczaj resetowania podrzędnych występuje po raz pierwszy pól w wierszu zmian w tabeli nadrzędnej.  
  
### <a name="to-cache-the-current-child-position"></a>Do pamięci podręcznej bieżące położenie elementów podrzędnych  
  
1.  Należy zadeklarować zmienną całkowitą do przechowywania położenie listy elementów podrzędnych i zmienną wartości logicznej do przechowywania, czy w pamięci podręcznej położenie elementów podrzędnych.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  Obsługa <xref:System.Windows.Forms.CurrencyManager.ListChanged> zdarzenia dla tego powiązania <xref:System.Windows.Forms.CurrencyManager> i sprawdź, czy <xref:System.ComponentModel.ListChangedType> z <xref:System.ComponentModel.ListChangedType.Reset>.  
  
3.  Sprawdź bieżącą pozycję <xref:System.Windows.Forms.CurrencyManager>. Jeśli jest większa niż pierwsza pozycja na liście (zazwyczaj 0), zapisz go do zmiennej.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  Obsługiwać listy nadrzędnych <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> zdarzenia nadrzędnego menedżera waluty. W obsłudze ustaw wartość logiczna wskazująca, że nie jest scenariusz buforowania. Jeśli <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> występuje zmiany do elementu nadrzędnego jest zmiana pozycji listy, a nie zmiany wartości elementu.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a>Aby zresetować położenie elementów podrzędnych  
  
1.  Obsługa <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> zdarzenia dla obiekt podrzędny powiązania <xref:System.Windows.Forms.CurrencyManager>.  
  
2.  Resetuj położenie elementów podrzędnych w tabeli w pamięci podręcznej miejsce zapisane w poprzedniej procedurze.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zapisać bieżącą pozycję w <xref:System.Windows.Forms.CurrencyManager>.for tabelą podrzędną i resetowanie położenia po zakończeniu edycji w tabeli nadrzędnej. Ten przykład zawiera dwa <xref:System.Windows.Forms.DataGridView> formanty powiązane z dwiema tabelami w <xref:System.Data.DataSet> przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. Ustanowieniu relacji między dwiema tabelami i Relacja jest dodawany do <xref:System.Data.DataSet>. Pozycja w tabeli podrzędnej jest początkowo ustawiona trzeciego wiersza w celach demonstracyjnych.  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 Aby przetestować przykładów kodu, wykonaj następujące czynności:  
  
1.  Można uruchomić przykład.  
  
2.  Upewnij się, że **pamięci podręcznej i resetowanie Umieść** pole wyboru jest zaznaczone.  
  
3.  Kliknij przycisk **pola nadrzędnego wyczyść** przycisk, aby spowodować zmiany w tabeli nadrzędnej. Należy zauważyć, że wybrany wiersz w tabeli podrzędnej nie ulega zmianie.  
  
4.  Zamknij i ponownie uruchomić przykład. Należy to zrobić, ponieważ spowoduje zresetowanie zachowanie tylko na pierwszej zmianie wiersza nadrzędnego.  
  
5.  Wyczyść **pamięci podręcznej i resetowanie Umieść** pole wyboru.  
  
6.  Kliknij przycisk **pola nadrzędnego wyczyść** przycisku. Należy zauważyć, że zmiany wybranego wiersza w tabeli podrzędnej w pierwszym wierszu.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, system.dane System.Drawing, System.Windows.Forms i zestawów System.XML.  
  
 Aby uzyskać informacje o sposobie budowania w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [csc.exe budynku wiersza polecenia z](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [BindingSource, składnik](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Wiązanie danych i formularzy Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
