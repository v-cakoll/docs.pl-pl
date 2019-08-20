---
title: Informacje o obiekcieC#wywołującym ()
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595340"
---
# <a name="caller-information-c"></a>Informacje o obiekcieC#wywołującym ()

Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego. Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.

Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną. W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> zdefiniowane w przestrzeni nazw:

|Atrybut|Opis|Typ|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka pliku w czasie kompilacji.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub właściwości obiektu wywołującego. Zobacz [nazwy członków](#member-names) w dalszej części tego tematu.|`String`|

## <a name="example"></a>Przykład

Poniższy przykład przedstawia, jak używać atrybutów informacji o obiekcie wywołującym. Dla każdego wywołania `TraceMessage` metody informacje o wywołującym są zastępowane jako argumenty parametrów opcjonalnych.

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
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a>Uwagi

Należy jawnie określić wartość domyślną dla każdego opcjonalnego parametru. Nie można zastosować atrybutów informacji o obiekcie wywołującym do parametrów, które nie są określone jako opcjonalne.

Atrybuty informacji o obiekcie wywołującym nie czynią parametru opcjonalnym. Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty.

Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji. W przeciwieństwie do wyników <xref:System.Exception.StackTrace%2A> właściwości dla wyjątków, nie ma to wpływu na wyniki.

Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.

### <a name="member-names"></a>Nazwy elementów członkowskich

Możesz użyć atrybutu, `CallerMemberName` aby uniknąć określania nazwy elementu członkowskiego `String` jako argumentu wywoływanej metody. Korzystając z tej techniki, można uniknąć problemu, którego **zmiana nazwy Refaktoryzacja** nie zmienia `String` wartości. Jest to szczególnie przydatne w następujących zadaniach:

- Używanie procedur do śledzenia i diagnostycznych.

- Implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu podczas wiązania danych. Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje. `CallerMemberName` Bez atrybutu, należy określić nazwę właściwości jako literału.

Poniższy wykres pokazuje nazwy elementów członkowskich, które są zwracane przy użyciu `CallerMemberName` atrybutu.

|Wywołanie ma miejsce w|Wynikowa nazwa elementu członkowskiego|
|-|-|
|Metoda, właściwość lub zdarzenie|Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.|
|Konstruktor|Ciąg „.ctor”|
|Statyczny konstruktor|Ciąg „.cctor”|
|Destruktor|Ciąg „Finalize”.|
|Zdefiniowane przez użytkownika operatory lub konwersje|Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.|
|Konstruktor atrybutu|Nazwa metody lub właściwości, do której zastosowano atrybut. Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.|
|Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)|Wartość domyślna opcjonalnego parametru.|

## <a name="see-also"></a>Zobacz także

- [Atrybuty (C#)](./attributes/index.md)
- [Atrybuty wspólne (C#)](./attributes/common-attributes.md)
- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [Koncepcje programowaniaC#()](./index.md)
