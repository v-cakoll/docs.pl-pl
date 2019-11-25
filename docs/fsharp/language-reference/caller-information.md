---
title: Informacje o obiekcie wywołującym
description: Opisuje sposób używania atrybutów argumentów informacji o wywołującym do uzyskiwania informacji o wywołującym z metody.
ms.date: 11/04/2019
ms.openlocfilehash: d995b37149277b7c7d1b6217ee484d3c90a7f8b3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976798"
---
# <a name="caller-information"></a>Informacje o obiekcie wywołującym

Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego. Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.

Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną. W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są zdefiniowane w przestrzeni nazw [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) :

|Atrybut|Opis|Typ|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka pliku w czasie kompilacji.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Nazwa metody lub właściwości obiektu wywołującego. Zobacz sekcję nazwy elementów członkowskich w dalszej części tego tematu.|`String`|

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można użyć tych atrybutów do śledzenia obiektu wywołującego.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member _.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a>Uwagi

Atrybuty informacji o wywołującym mogą być stosowane tylko do parametrów opcjonalnych. Atrybuty informacji o wywołującym powodują, że kompilator zapisuje odpowiednią wartość dla każdego opcjonalnego parametru uzupełnionego atrybutem informacje o wywołującym.

Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji. W przeciwieństwie do wyników właściwości [ślad stosu](/dotnet/api/system.diagnostics.stacktrace) dla wyjątków, nie ma to wpływu na wyniki.

Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.

## <a name="member-names"></a>Nazwy elementów członkowskich

Można użyć atrybutu [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) , aby uniknąć określania nazwy elementu członkowskiego jako argumentu `String` dla wywoływanej metody. Korzystając z tej techniki, można uniknąć problemu, którego Refaktoryzacja zmiany nazwy nie zmienia wartości `String`. Jest to szczególnie przydatne w następujących zadaniach:

- Używanie procedur do śledzenia i diagnostycznych.
- Implementowanie interfejsu [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) podczas wiązania danych. Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje. Bez atrybutu [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) należy określić nazwę właściwości jako literału.

Poniższy wykres pokazuje nazwy elementów członkowskich, które są zwracane w przypadku używania atrybutu CallerMemberName.

|Wywołanie ma miejsce w|Wynikowa nazwa elementu członkowskiego|
|-------------------|------------------|
|Metoda, właściwość lub zdarzenie|Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.|
|Konstruktor|Ciąg „.ctor”|
|Statyczny konstruktor|Ciąg „.cctor”|
|Destruktor|Ciąg „Finalize”.|
|Zdefiniowane przez użytkownika operatory lub konwersje|Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.|
|Konstruktor atrybutu|Nazwa elementu członkowskiego, do którego został zastosowany atrybut. Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.|
|Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)|Wartość domyślna opcjonalnego parametru.|

## <a name="see-also"></a>Zobacz także

- [Atrybuty](attributes.md)
- [Nazwane argumenty](parameters-and-arguments.md#named-arguments)
- [Parametry opcjonalne](parameters-and-arguments.md#optional-parameters)
