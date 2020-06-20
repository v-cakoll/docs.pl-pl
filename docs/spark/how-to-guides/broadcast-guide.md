---
title: Używanie zmiennych emisji w programie .NET dla Apache Spark
description: Dowiedz się, jak używać zmiennych emisji w programie .NET dla aplikacji Apache Spark.
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 391e32cda14a9b3186ac96800351ddcb39a3d359
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105605"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a>Używanie zmiennych emisji w programie .NET dla Apache Spark

W tym artykule dowiesz się, jak używać zmiennych emisji w programie .NET dla Apache Spark. [Zmienne emisji w Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) są mechanizmami do udostępniania zmiennych w ramach wykonawców, które są przeznaczone tylko do odczytu. Zmienne emisji umożliwiają zachowanie zmiennej tylko do odczytu w pamięci podręcznej na poszczególnych maszynach, a nie dostarczenie kopii jej z zadaniami. Zmiennych emisji można użyć, aby przydzielić każdemu węzłowi kopię dużego wejściowego zestawu danych w efektywny sposób.

Ponieważ dane są wysyłane tylko raz, zmienne emisji mają korzyści z wydajności w porównaniu do zmiennych lokalnych, które są wysyłane do modułów wykonujących wszystkie zadania. Zapoznaj się z [dokumentacją oficjalną zmienna emisji](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) , aby lepiej zrozumieć zmienne emisji i dlaczego są one używane.

## <a name="create-broadcast-variables"></a>Utwórz zmienne emisji

Aby utworzyć zmienną emisji, wywołaj `SparkContext.Broadcast(v)` dla każdej zmiennej `v` . Zmienna emisji jest otoką wokół zmiennej `v` , a jej wartość jest dostępna poprzez wywołanie `Value()` metody.

W poniższym fragmencie kodu `v` zostanie utworzona zmienna ciągu, a zmienna emisji `bv` jest tworzona, gdy `SparkContext.Broadcast(v)` jest wywoływana. Zwróć uwagę na parametr typu dla parametru, który jest `Broadcast` zgodny z typem rozgłaszanej zmiennej. Funkcja zdefiniowana przez użytkownika (UDF) zwraca wartość `bv` .

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a>Usuń zmienne emisji

Zmienną emisji można usunąć ze wszystkich modułów wykonujących, wywołując `Destroy()` metodę.

```csharp
bv.Destroy();
```

`Destroy()`usuwa wszystkie dane i metadane związane ze zmienną emisji i powinny być używane z zachowaniem ostrożności. Gdy zmienna emisji zostanie zniszczona, nie można jej użyć ponownie.

## <a name="limit-broadcast-variable-scope-in-udfs"></a>Ogranicz zakres zmiennej emisji w UDF

W przypadku używania zmiennych emisji w UDF należy ograniczyć zakres zmiennej tylko do formatu UDF, który odwołuje się do zmiennej. [Przewodnik po użyciu UDF](udf-guide.md) zawiera szczegółowy opis tego zjawiska. Zakres jest szczególnie decydujący podczas wywoływania `Destroy()` zmiennej emisji.

Jeśli zmienna emisji, która została zniszczona, jest widoczna dla innych UDF lub dostępna z niej, jest pobierana do serializacji przez wszystkie UDF, nawet jeśli nie odwołują się do nich. Platforma .NET dla Apache Spark nie może serializować zniszczonej zmiennej emisji, co spowoduje wystąpienie błędu. Poniższy fragment kodu ilustruje ten błąd:

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

// Using the broadcast variable in a UDF:
Func<Column, Column> udf1 = Udf<string, string>(
    str => $"{str}: {bv.Value()}");

// Destroying bv
bv.Destroy();

// Calling udf1 after destroying bv throws the following expected exception:
// org.apache.spark.SparkException: Attempted to use Broadcast(0) after it was destroyed
df.Select(udf1(df["_1"])).Show();

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 throws the following (unexpected) exception:
// [Error] [JvmBridge] org.apache.spark.SparkException: Task not serializable
df.Select(udf2(df["_1"])).Show();
```

Poniższy fragment kodu pokazuje, jak upewnić się, że niszczenie `bv` nie ma wpływu na `udf2` skutek nieoczekiwanego zachowania serializacji:

```csharp
string v = "Variable to be broadcasted";
// Restricting the visibility of bv to only the UDF referencing it
{
    Broadcast<string> bv = SparkContext.Broadcast(v);

    // Using the broadcast variable in a UDF:
    Func<Column, Column> udf1 = Udf<string, string>(
        str => $"{str}: {bv.Value()}");

    // Destroying bv
    bv.Destroy();
}

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 works fine as expected
df.Select(udf2(df["_1"])).Show();
```

## <a name="next-steps"></a>Następne kroki

* [Wprowadzenie do platformy .NET dla Apache Spark](../tutorials/get-started.md)
* [Debugowanie aplikacji .NET dla Apache Spark w systemie Windows](debug.md)
* [Wdróż platformę .NET dla Apache Spark procesów roboczych i plików binarnych funkcji zdefiniowanych przez użytkownika](deploy-worker-udf-binaries.md)
