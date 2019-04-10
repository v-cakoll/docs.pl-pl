---
title: Informacje o wywołującym
description: Opisuje sposób używania Caller — atrybuty Argument informacji, aby uzyskać informacje o wywołującym z metody.
ms.date: 04/25/2017
ms.openlocfilehash: 13092df453b684d3ed4a93c842ea49c066157cb6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316157"
---
# <a name="caller-information"></a>Informacje o wywołującym

Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego. Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.

Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną. W poniższej tabeli przedstawiono atrybuty informacji o obiekcie wywołującym, które są zdefiniowane w [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) przestrzeni nazw:

|Atrybut|Opis|Typ|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka pliku w czasie kompilacji.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Nazwa metody lub właściwości obiektu wywołującego. Zobacz sekcję nazwy elementów członkowskich w dalszej części tego tematu.|`String`|

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można wykorzystać te atrybuty do śledzenia obiekt wywołujący.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a>Uwagi

Caller — atrybuty informacji dotyczą wyłącznie następujące parametry opcjonalne. Atrybuty informacji o obiekcie wywołującym spowodować, że kompilator, aby zapisać odpowiednie wartości dla każdego opcjonalnego parametru dekorowane za pomocą atrybutów informacji o obiekcie wywołującym.

Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji. W przeciwieństwie do wyników [ślad stosu](/dotnet/api/system.diagnostics.stacktrace) właściwość dla wyjątków, na wyniki nie ma wpływu zasłanianie.

Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.

## <a name="member-names"></a>Nazwy elementów członkowskich

Możesz użyć [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atrybutu, aby uniknąć określania nazwy elementu członkowskiego jako `String` argument wywoływanej metody. Korzystając z tej techniki, można uniknąć problemu, który Refaktoryzacja zmiany nazwy nie zmienia `String` wartości. Jest to szczególnie przydatne w następujących zadaniach:

* Używanie procedur do śledzenia i diagnostycznych.
* Implementowanie [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interfejs podczas wiązania danych. Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje. Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atrybutu, należy określić nazwę właściwości jako literał.

Na poniższym wykresie przedstawiono elementu członkowskiego nazw, które są zwracane, gdy używasz atrybutu CallerMemberName.

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
- [Argumenty nazwane](parameters-and-arguments.md#named-arguments)
- [Następujące parametry opcjonalne](parameters-and-arguments.md#optional-parameters)
