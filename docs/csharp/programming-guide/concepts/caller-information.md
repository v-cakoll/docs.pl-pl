---
title: Informacje o wywołującym (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 048e91ad337f74ef04a2a03412a44a0be0ef9506
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560743"
---
# <a name="caller-information-c"></a>Informacje o wywołującym (C#)
Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego. Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.  
  
 Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną. W poniższej tabeli przedstawiono atrybuty informacji o obiekcie wywołującym, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka pliku w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub właściwości obiektu wywołującego. Zobacz [nazwy elementów członkowskich](#MEMBERNAMES) w dalszej części tego tematu.|`String`|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia, jak używać atrybutów informacji o obiekcie wywołującym. Przy każdym wywołaniu `TraceMessage` metody, informacje o wywołującym są podstawiane jako argumenty opcjonalnych parametrów.  
  
```csharp  
public void DoProcessing()  
{  
    TraceMessage("Something happened.");  
}  
  
public void TraceMessage(string message,  
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",  
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",  
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)  
{  
    System.Diagnostics.Trace.WriteLine("message: " + message);  
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);  
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);  
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);  
}  
  
// Sample Output:  
//  message: Something happened.  
//  member name: DoProcessing  
//  source file path: c:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoCS\CallerInfoCS\Form1.cs  
//  source line number: 31  
```  
  
## <a name="remarks"></a>Uwagi  
 Należy jawnie określić wartość domyślną dla każdego opcjonalnego parametru. Nie można zastosować atrybutów informacji o obiekcie wywołującym do parametrów, które nie są określone jako opcjonalne.  
  
 Atrybuty informacji o obiekcie wywołującym nie czynią parametru opcjonalnym. Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty.  
  
 Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji. W przeciwieństwie do wyników <xref:System.Exception.StackTrace%2A> właściwość dla wyjątków, na wyniki nie ma wpływu zasłanianie.  
  
 Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.  
  
###  <a name="MEMBERNAMES"></a> Nazwy elementów członkowskich  
 Możesz użyć `CallerMemberName` atrybutu, aby uniknąć określania nazwy elementu członkowskiego jako `String` argument wywoływanej metody. Korzystając z tej techniki, można uniknąć problemu, **Refaktoryzacja zmiany nazwy** nie zmienia `String` wartości. Jest to szczególnie przydatne w następujących zadaniach:  
  
-   Używanie procedur do śledzenia i diagnostycznych.  
  
-   Implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejs podczas wiązania danych. Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje. Bez `CallerMemberName` atrybutu, należy określić nazwę właściwości jako literał.  
  
 W poniższej tabeli przedstawiono składowej, nazwy, które są zwracane, gdy używasz `CallerMemberName` atrybutu.  
  
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

- [Atrybuty (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)  
- [Atrybuty wspólne (C#)](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
- [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [Koncepcje programowania (C#)](../../../csharp/programming-guide/concepts/index.md)
