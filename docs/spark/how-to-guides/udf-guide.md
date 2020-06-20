---
title: Tworzenie funkcji zdefiniowanych przez użytkownika (UDF) w programie .NET dla Apache Spark
description: Dowiedz się, jak zaimplementować funkcje zdefiniowane przez użytkownika (UDF) w programie .NET dla aplikacji Apache Spark.
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 96597c7e2d45dfdf8406b0d3e80daad270996b97
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105602"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a>Tworzenie funkcji zdefiniowanych przez użytkownika (UDF) w programie .NET dla Apache Spark

W tym artykule dowiesz się, jak używać funkcji zdefiniowanych przez użytkownika (UDF) w programie .NET dla Apache Spark. [UDF)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) są funkcją platformy Spark, która umożliwia korzystanie z funkcji niestandardowych w celu zwiększenia wbudowanej funkcji systemu. UDF Przekształć wartości z pojedynczego wiersza w tabeli, aby utworzyć jedną odpowiednią wartość wyjściową dla każdego wiersza w oparciu o logikę zdefiniowaną w elemencie UDF.

## <a name="define-udfs"></a>Zdefiniuj UDF

Zapoznaj się z następującą definicją UDF:

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

Format UDF przyjmuje `string` jako dane wejściowe w postaci [kolumny](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) tabeli [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) i zwraca `string` z `hello` dołączonymi przed danymi wejściowymi.

Następująca ramka Dataframe `df` zawiera listę nazw:

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

Teraz zastosujemy powyższe zdefiniowane `udf` do ramki Dataframe `df` :

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

Następująca ramka danych `udfResult` jest wynikiem UDF:

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

Aby lepiej zrozumieć, jak wdrożyć UDF, przejrzyj [funkcje pomocnika UDF](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) i [przykłady](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) w witrynie GitHub.

## <a name="udf-serialization"></a>Serializacja UDF

Ponieważ UDF są funkcjami, które muszą być wykonywane na procesach roboczych, muszą być serializowane i wysyłane do procesów roboczych w ramach ładunku ze sterownika. [Delegat](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/delegates/), który jest odwołaniem do metody, musi być serializowany, a jego [obiektem docelowym](https://docs.microsoft.com/en-us/dotnet/api/system.delegate.target?view=netframework-4.8) jest wystąpienie klasy, dla którego bieżący delegat wywołuje metodę wystąpienia. Zapoznaj się z tym [przykładem kodu w usłudze GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) , aby lepiej zrozumieć sposób wykonywania serializacji UDF.

Platforma .NET dla Apache Spark używa platformy .NET Core, która nie obsługuje serializacji delegatów. Zamiast tego odbicie jest używane do serializacji obiektu docelowego, gdzie jest zdefiniowany delegat. Gdy wiele delegatów jest zdefiniowanych w wspólnym zakresie, mają one miejsce do użycia, które stają się celem odbicia w celu serializacji.

### <a name="serialization-example"></a>Przykład serializacji

Poniższy fragment kodu definiuje dwa zmienne String, do których odwołuje się dwóch delegatów funkcji, które zwracają odpowiednie ciągi w wyniku:

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

Powyższy kod C# generuje następujący kod w języku C# ( [sharplab.IO](https://sharplab.io)) z kompilatora:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

Oba te `func` i `func2` korzystają z tego samego zamknięcia `<>c__DisplayClass0_0` , czyli elementu docelowego, który jest serializowany podczas serializacji delegatów `func` i `func2` . Chociaż `Func<string, string> a` tylko odwołuje się do niego `s1` , `s2` również jest serializowany, gdy bajty są wysyłane do pracowników.

Może to prowadzić do nieoczekiwanych zachowań w czasie wykonywania (takich jak w przypadku używania [zmiennych emisji](broadcast-guide.md)), co oznacza, że zaleca się ograniczenie widoczności zmiennych używanych w funkcji do zakresu tej funkcji.

Poniższy fragment kodu jest zalecanym sposobem wdrożenia żądanego zachowania serializacji:

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

Powyższy kod C# generuje następujący kod w języku C# ( [sharplab.IO](https://sharplab.io)) z kompilatora:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

Zwróć uwagę na to, że `func` `func2` nie ma już wolnego zamknięcia i że mają własne osobne `<>c__DisplayClass0_0` zamknięcia `<>c__DisplayClass0_1` . Gdy jest używany jako element docelowy dla serializacji, żadne inne niż zmienne, do których się odwołuje, zostaną zserializowane dla delegata. Takie zachowanie jest ważne, aby zachować świadomość podczas implementowania wielu UDF w wspólnym zakresie.

## <a name="some-spark-udf-caveats"></a>Niektóre ograniczenia UDF dla platformy Spark

* Wartości null w UDF mogą generować wyjątki. Jest on odpowiedzialny za ich obsługę.
* UDF nie wykorzystuje optymalizacji dostarczonych przez funkcje wbudowane platformy Spark, dlatego zaleca się używanie wbudowanych funkcji, jeśli jest to możliwe.

## <a name="next-steps"></a>Następne kroki

* [Wprowadzenie do platformy .NET dla Apache Spark](../tutorials/get-started.md)
* [Debugowanie aplikacji .NET dla Apache Spark w systemie Windows](debug.md)
