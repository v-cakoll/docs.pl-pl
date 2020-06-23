---
title: Tworzenie funkcji zdefiniowanych przez użytkownika (UDF) w programie .NET dla Apache Spark
description: Dowiedz się, jak zaimplementować funkcje zdefiniowane przez użytkownika (UDF) w programie .NET dla aplikacji Apache Spark.
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: fe3dec187f94f84adb1217c39ff6aabc4b4db1c5
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142020"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="73dfd-103">Tworzenie funkcji zdefiniowanych przez użytkownika (UDF) w programie .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="73dfd-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="73dfd-104">W tym artykule dowiesz się, jak używać funkcji zdefiniowanych przez użytkownika (UDF) w programie .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="73dfd-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="73dfd-105">[UDF)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) są funkcją platformy Spark, która umożliwia korzystanie z funkcji niestandardowych w celu zwiększenia wbudowanej funkcji systemu.</span><span class="sxs-lookup"><span data-stu-id="73dfd-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="73dfd-106">UDF Przekształć wartości z pojedynczego wiersza w tabeli, aby utworzyć jedną odpowiednią wartość wyjściową dla każdego wiersza w oparciu o logikę zdefiniowaną w elemencie UDF.</span><span class="sxs-lookup"><span data-stu-id="73dfd-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

## <a name="define-udfs"></a><span data-ttu-id="73dfd-107">Zdefiniuj UDF</span><span class="sxs-lookup"><span data-stu-id="73dfd-107">Define UDFs</span></span>

<span data-ttu-id="73dfd-108">Zapoznaj się z następującą definicją UDF:</span><span class="sxs-lookup"><span data-stu-id="73dfd-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="73dfd-109">Format UDF przyjmuje `string` jako dane wejściowe w postaci [kolumny](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) tabeli [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) i zwraca `string` z `hello` dołączonymi przed danymi wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="73dfd-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="73dfd-110">Następująca ramka Dataframe `df` zawiera listę nazw:</span><span class="sxs-lookup"><span data-stu-id="73dfd-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="73dfd-111">Teraz zastosujemy powyższe zdefiniowane `udf` do ramki Dataframe `df` :</span><span class="sxs-lookup"><span data-stu-id="73dfd-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="73dfd-112">Następująca ramka danych `udfResult` jest wynikiem UDF:</span><span class="sxs-lookup"><span data-stu-id="73dfd-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="73dfd-113">Aby lepiej zrozumieć, jak wdrożyć UDF, przejrzyj [funkcje pomocnika UDF](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) i [przykłady](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="73dfd-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="73dfd-114">Serializacja UDF</span><span class="sxs-lookup"><span data-stu-id="73dfd-114">UDF serialization</span></span>

<span data-ttu-id="73dfd-115">Ponieważ UDF są funkcjami, które muszą być wykonywane na procesach roboczych, muszą być serializowane i wysyłane do procesów roboczych w ramach ładunku ze sterownika.</span><span class="sxs-lookup"><span data-stu-id="73dfd-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="73dfd-116">[Delegat](../../csharp/programming-guide/delegates/index.md), który jest odwołaniem do metody, musi być serializowany oraz jego [obiekt docelowy](xref:System.Delegate.Target%2A), który jest wystąpieniem klasy, na którym bieżący delegat wywołuje metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="73dfd-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="73dfd-117">Zapoznaj się z tym [przykładem kodu w usłudze GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) , aby lepiej zrozumieć sposób wykonywania serializacji UDF.</span><span class="sxs-lookup"><span data-stu-id="73dfd-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="73dfd-118">Platforma .NET dla Apache Spark używa platformy .NET Core, która nie obsługuje serializacji delegatów.</span><span class="sxs-lookup"><span data-stu-id="73dfd-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="73dfd-119">Zamiast tego odbicie jest używane do serializacji obiektu docelowego, gdzie jest zdefiniowany delegat.</span><span class="sxs-lookup"><span data-stu-id="73dfd-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="73dfd-120">Gdy wiele delegatów jest zdefiniowanych w wspólnym zakresie, mają one miejsce do użycia, które stają się celem odbicia w celu serializacji.</span><span class="sxs-lookup"><span data-stu-id="73dfd-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="73dfd-121">Przykład serializacji</span><span class="sxs-lookup"><span data-stu-id="73dfd-121">Serialization example</span></span>

<span data-ttu-id="73dfd-122">Poniższy fragment kodu definiuje dwa zmienne String, do których odwołuje się dwóch delegatów funkcji, które zwracają odpowiednie ciągi w wyniku:</span><span class="sxs-lookup"><span data-stu-id="73dfd-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

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

<span data-ttu-id="73dfd-123">Powyższy kod C# generuje następujący kod w języku C# ( [sharplab.IO](https://sharplab.io)) z kompilatora:</span><span class="sxs-lookup"><span data-stu-id="73dfd-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="73dfd-124">Oba te `func` i `func2` korzystają z tego samego zamknięcia `<>c__DisplayClass0_0` , czyli elementu docelowego, który jest serializowany podczas serializacji delegatów `func` i `func2` .</span><span class="sxs-lookup"><span data-stu-id="73dfd-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="73dfd-125">Chociaż `Func<string, string> a` tylko odwołuje się do niego `s1` , `s2` również jest serializowany, gdy bajty są wysyłane do pracowników.</span><span class="sxs-lookup"><span data-stu-id="73dfd-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="73dfd-126">Może to prowadzić do nieoczekiwanych zachowań w czasie wykonywania (takich jak w przypadku używania [zmiennych emisji](broadcast-guide.md)), co oznacza, że zaleca się ograniczenie widoczności zmiennych używanych w funkcji do zakresu tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="73dfd-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="73dfd-127">Poniższy fragment kodu jest zalecanym sposobem wdrożenia żądanego zachowania serializacji:</span><span class="sxs-lookup"><span data-stu-id="73dfd-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

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

<span data-ttu-id="73dfd-128">Powyższy kod C# generuje następujący kod w języku C# ( [sharplab.IO](https://sharplab.io)) z kompilatora:</span><span class="sxs-lookup"><span data-stu-id="73dfd-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="73dfd-129">Zwróć uwagę na to, że `func` `func2` nie ma już wolnego zamknięcia i że mają własne osobne `<>c__DisplayClass0_0` zamknięcia `<>c__DisplayClass0_1` .</span><span class="sxs-lookup"><span data-stu-id="73dfd-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="73dfd-130">Gdy jest używany jako element docelowy dla serializacji, żadne inne niż zmienne, do których się odwołuje, zostaną zserializowane dla delegata.</span><span class="sxs-lookup"><span data-stu-id="73dfd-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="73dfd-131">Takie zachowanie jest ważne, aby zachować świadomość podczas implementowania wielu UDF w wspólnym zakresie.</span><span class="sxs-lookup"><span data-stu-id="73dfd-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="73dfd-132">Niektóre ograniczenia UDF dla platformy Spark</span><span class="sxs-lookup"><span data-stu-id="73dfd-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="73dfd-133">Wartości null w UDF mogą generować wyjątki.</span><span class="sxs-lookup"><span data-stu-id="73dfd-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="73dfd-134">Jest on odpowiedzialny za ich obsługę.</span><span class="sxs-lookup"><span data-stu-id="73dfd-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="73dfd-135">UDF nie wykorzystuje optymalizacji dostarczonych przez funkcje wbudowane platformy Spark, dlatego zaleca się używanie wbudowanych funkcji, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="73dfd-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="next-steps"></a><span data-ttu-id="73dfd-136">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="73dfd-136">Next steps</span></span>

* [<span data-ttu-id="73dfd-137">Wprowadzenie do platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="73dfd-137">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="73dfd-138">Debugowanie aplikacji .NET dla Apache Spark w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="73dfd-138">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
