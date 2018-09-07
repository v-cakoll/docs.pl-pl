---
title: 'Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: d0bb41da69bf1cb87f052c11d3a7d1f1783320ad
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080169"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a>Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych
Często wyjątków i błędów występujących na obiekty źródłowe firm gdy powiązanie z kontrolkami. Możesz przechwytywać te błędy i wyjątki i następnie odzyskać lub przekazać informacje o błędzie dla użytkownika, obsługując <xref:System.Windows.Forms.Binding.BindingComplete> zdarzeń dla określonego <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, lub <xref:System.Windows.Forms.CurrencyManager> składnika.  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu demonstruje sposób obsługi błędów i wyjątków występujących podczas operacji powiązanie danych. Demonstracja przechwytywać błędy obsługi <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenia <xref:System.Windows.Forms.Binding> obiektów. Aby przechwycić błędów i wyjątków, obsługa tego zdarzenia, należy włączyć formatowania dla wiązania. Możesz włączyć formatowanie powiązania jest tworzony lub dodanie do kolekcji powiązania lub poprzez skonfigurowanie <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> właściwość `true`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 Podczas wykonywania kodu i ciągiem pustym wprowadzonej w mniej niż 100 nazwę części lub wartość jest wprowadzana numeru części pojawi się okno komunikatu. Jest to wynik obsługi <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenia dla tych powiązań pola tekstowego.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)
