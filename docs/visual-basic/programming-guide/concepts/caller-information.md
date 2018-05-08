---
title: Informacje o wywołującym (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 0074ad5bfa5907fb1d02cc92b8b5717897a36b3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="caller-information-visual-basic"></a>Informacje o wywołującym (Visual Basic)
Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego. Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.  
  
 Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną. Poniższa tabela zawiera listę atrybutów wywołującego informacje, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka pliku w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub właściwości obiektu wywołującego. Zobacz [nazwy elementów członkowskich](#MEMBERNAMES) dalszej części tego tematu.|`String`|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak używać atrybutów informacji o obiekcie wywołującym. Na każde wywołanie `TraceMessage` zastępuje metodę, informacje o wywołującym jako argumenty następujące parametry opcjonalne.  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a>Uwagi  
 Należy jawnie określić wartość domyślną dla każdego opcjonalnego parametru. Nie można zastosować atrybutów informacji o obiekcie wywołującym do parametrów, które nie są określone jako opcjonalne.  
  
 Atrybuty informacji o obiekcie wywołującym nie czynią parametru opcjonalnym. Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty.  
  
 Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji. W odróżnieniu od wyników <xref:System.Exception.StackTrace%2A> właściwości wyjątki, wyniki nie dotyczą zaciemnienie.  
  
 Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.  
  
###  <a name="MEMBERNAMES"></a> Nazwy elementów członkowskich  
 Można użyć `CallerMemberName` atrybutu, aby uniknąć, określając nazwę elementu członkowskiego jako `String` argument wywołaną metodę. Przy użyciu tej metody, można uniknąć który **zmienić refaktoryzacji** nie ulega zmianie `String` wartości. Jest to szczególnie przydatne w następujących zadaniach:  
  
-   Używanie procedur do śledzenia i diagnostycznych.  
  
-   Implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu podczas wiązania danych. Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje. Bez `CallerMemberName` atrybutu, należy określić nazwę właściwości jako literału.  
  
 W poniższej tabeli przedstawiono element członkowski nazw, które są zwracane, gdy używasz `CallerMemberName` atrybutu.  
  
|Wywołanie ma miejsce w|Wynikowa nazwa elementu członkowskiego|  
|-------------------------|------------------------|  
|Metoda, właściwość lub zdarzenie|Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.|  
|Konstruktor|Ciąg „.ctor”|  
|Statyczny konstruktor|Ciąg „.cctor”|  
|Destruktor|Ciąg „Finalize”.|  
|Zdefiniowane przez użytkownika operatory lub konwersje|Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.|  
|Konstruktor atrybutu|Nazwa elementu członkowskiego, do którego został zastosowany atrybut. Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.|  
|Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)|Wartość domyślna opcjonalnego parametru.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty (Visual Basic)](../../../visual-basic/language-reference/attributes.md)  
 [Atrybuty wspólne (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
 [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Koncepcje programowania (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
