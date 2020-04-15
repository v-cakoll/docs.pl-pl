---
title: 'Atrybuty zastrzeżone języka C#: śledzenie informacji o dzwoniącym'
ms.date: 04/09/2020
description: Te atrybuty instruują kompilator do generowania informacji o kodzie, który wywołuje członka. Do dostarczania szczegółowych informacji śledzenia za pomocą callerfilepath, CallerLineNumber i CallerMemberName
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389878"
---
# <a name="reserved-attributes-determine-caller-information"></a>Atrybuty zarezerwowane: określanie informacji o dzwoniącym

Za pomocą atrybutów informacji można uzyskać informacje o wywołującym do metody. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę członka wywołującego. Aby uzyskać informacje o wywołującym element członkowski, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych. Każdy parametr opcjonalny określa wartość domyślną. W poniższej tabeli wymieniono atrybuty <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informacje o dzwoniącym zdefiniowane w obszarze nazw:

|Atrybut|Opis|Typ|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Pełna ścieżka jest ścieżką w czasie kompilacji.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub nazwa właściwości obiektu wywołującego.|`String`|

Te informacje ułatwiają pisanie śledzenia, debugowania i tworzenia narzędzi diagnostycznych. W poniższym przykładzie pokazano, jak używać atrybutów informacji o wywołującym. Przy każdym wywołaniu `TraceMessage` metody informacje o wywołującym są zastępowane jako argumenty parametrów opcjonalnych.

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

Można określić jawną wartość domyślną dla każdego parametru opcjonalnego. Nie można zastosować atrybutów informacji o wywołującym do parametrów, które nie są określone jako opcjonalne. Atrybuty informacji wywołującego nie sprawiają, że parametr jest opcjonalny. Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty. Wartości informacji wywołującego są emitowane jako literały do języka pośredniego (IL) w czasie kompilacji. W przeciwieństwie do <xref:System.Exception.StackTrace%2A> wyników właściwości dla wyjątków, wyniki nie są narażone na zaciemnienie. Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.

### <a name="member-names"></a>Nazwy członków

Można użyć `CallerMemberName` atrybutu, aby uniknąć określania `String` nazwy elementu członkowskiego jako argumentu do metody wywoływane. Korzystając z tej techniki, można uniknąć problemu, który **rename refaktoryzacji** nie zmienia `String` wartości. Jest to szczególnie przydatne w następujących zadaniach:

- Używanie procedur do śledzenia i diagnostycznych.
- Implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu podczas wiązania danych. Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje. Bez `CallerMemberName` atrybutu należy określić nazwę właściwości jako literał.

Na poniższym wykresie przedstawiono nazwy członków, które są zwracane podczas korzystania z atrybutu. `CallerMemberName`

|Połączenia następować są w ciągu|Wynikowa nazwa elementu członkowskiego|
|-|-|
|Metoda, właściwość lub zdarzenie|Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.|
|Konstruktor|Ciąg „.ctor”|
|Statyczny konstruktor|Ciąg „.cctor”|
|Destruktor|Ciąg „Finalize”.|
|Zdefiniowane przez użytkownika operatory lub konwersje|Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.|
|Konstruktor atrybutu|Nazwa metody lub właściwości, do której jest stosowany atrybut. Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.|
|Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)|Wartość domyślna opcjonalnego parametru.|

## <a name="see-also"></a>Zobacz też

- [Argumenty nazwane i opcjonalne](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [Atrybuty](../../../standard/attributes/index.md)
