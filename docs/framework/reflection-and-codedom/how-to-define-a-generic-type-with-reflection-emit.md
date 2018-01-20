---
title: "Porady: definiowanie typu ogólnego przy użyciu emisji odbicia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6096a54c6a530035bd32c24d427ba047f905476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Porady: definiowanie typu ogólnego przy użyciu emisji odbicia
W tym temacie przedstawiono sposób tworzenia prostego typu ogólnego z dwoma parametrami typu, jak zastosować ograniczenia klasy, interfejsu, ograniczenia i ograniczeń specjalnych do parametrów typu i sposobu tworzenia elementów członkowskich, które używają parametrów typu klasy jako typy parametrów i zwracanych typów.  
  
> [!IMPORTANT]
>  Metoda nie jest rodzajowa tak, ponieważ należy do typu ogólnego i używa parametrów typu tego typu. Metody jest rodzajowy, tylko wtedy, gdy ma własną listy parametrów typu. Większość metody na typach ogólnych nie są ogólny, jak w poniższym przykładzie. Na przykład emitowania metody rodzajowej zobacz [porady: definiowanie metody ogólnej przy emisja odbicia](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Aby zdefiniować typu ogólnego  
  
1.  Zdefiniuj zestawie dynamicznym o nazwie `GenericEmitExample1`. W tym przykładzie zestaw jest wykonywane i zapisywane na dysku, dlatego <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> jest określona.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  Zdefiniuj module dynamicznym. Zestaw składa się z modułów pliku wykonywalnego. Dla zestawu jednego modułu Nazwa modułu jest taka sama jak nazwa zestawu i nazwa pliku jest nazwa modułu oraz rozszerzenia.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  Zdefiniuj klasę. W tym przykładzie klasa o nazwie `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  Zdefiniuj parametry typu ogólnego `Sample` przez przekazanie tablica ciągów zawierająca nazwy parametrów w celu <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> metody. Dzięki temu klasy typu ogólnego. Wartość zwracana jest tablicą <xref:System.Reflection.Emit.GenericTypeParameterBuilder> obiekty reprezentujące parametrów typu, które mogą być używane w kodzie emitowany.  
  
     W poniższym kodzie `Sample` staje się typem ogólnym z parametrami typu `TFirst` i `TSecond`. Aby czytelność kodu, każdy <xref:System.Reflection.Emit.GenericTypeParameterBuilder> znajduje się w zmiennej z taką samą nazwę jak parametr typu.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  Dodaj ograniczeń specjalnych parametrów typu. W tym przykładzie parametr typu `TFirst` jest ograniczone do typów, które mają konstruktorów bez parametrów i typy referencyjne.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  Opcjonalnie można dodać ograniczenia klasy i interfejs do parametrów typu. W tym przykładzie parametr typu `TFirst` jest ograniczona do typów wyprowadzonych z klasy podstawowej reprezentowany przez <xref:System.Type> obiektów zawartych w zmiennej `baseType`, i implementują interfejsy, których typy są zawarte w zmiennych `interfaceA` i `interfaceB`. Zobacz przykład kodu dla deklaracji i przypisanie tych zmiennych.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  Zdefiniuj pola. W tym przykładzie typ pola jest określony przez parametr typu `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder>pochodną <xref:System.Type>, dzięki czemu można używać parametrów typu ogólnego, można użyć typu dowolnego miejsca.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  Zdefiniuj metody, która używa parametrów typu ogólnego typu. Należy pamiętać, że takie metody nie są ogólny, chyba że mają własne listy parametrów typu. Poniższy kod definiuje `static` — metoda (`Shared` w języku Visual Basic) pobierającej tablicę `TFirst` i zwraca `List<TFirst>` (`List(Of TFirst)` w języku Visual Basic) zawierający wszystkie elementy tablicy. Aby zdefiniować tej metody, należy utworzyć typ `List<TFirst>` przez wywołanie metody <xref:System.Type.MakeGenericType%2A> w definicji typu ogólnego `List<T>`. ( `T` Zostanie pominięty, gdy używasz `typeof` — operator (`GetType` w języku Visual Basic) można pobrać definicji typu ogólnego.) Typ parametru jest tworzona przy użyciu <xref:System.Type.MakeArrayType%2A> metody.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Emituj treści metody. Treści metody składa się z trzech kody operacji, które ładują tablicy wejściowej na stosie, należy wywołać `List<TFirst>` konstruktora przyjmującego `IEnumerable<TFirst>` (które wykonuje całą pracę umieszczania elementów wejściowych na liście) i zwróć (pozostawiając nowe <xref:System.Collections.Generic.List%601> obiektu na stosie). Trudne część emitowanie ten kod będzie niedługo konstruktora.  
  
     <xref:System.Type.GetConstructor%2A> Metoda nie jest obsługiwana na <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, więc nie można pobrać konstruktora `List<TFirst>` bezpośrednio. Najpierw należy pobrać konstruktora definicji typu ogólnego `List<T>` , a następnie wywołaj metodę, który konwertuje go do odpowiedniego konstruktora `List<TFirst>`.  
  
     Konstruktor używany w tym przykładzie kodu pobiera `IEnumerable<T>`. Należy jednak pamiętać, że nie jest definicji typu ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejs ogólny; zamiast tego parametru typu `T` z `List<T>` musi zastąpić dla parametru typu `T` z `IEnumerable<T>`. (Prawdopodobnie mylące tylko, ponieważ oba typy ma parametry typu o nazwie `T`. That is, dlaczego w tym przykładzie kodu używane nazwy `TFirst` i `TSecond`.) Aby uzyskać typu argumentu konstruktora, uruchom przy użyciu definicji typu ogólnego `IEnumerable<T>` i Wywołaj <xref:System.Type.MakeGenericType%2A> z pierwszy parametr typu ogólnego `List<T>`. Lista argumentów konstruktora muszą być przekazywane jako tablica, z tylko jednym argumentem. w takim przypadku.  
  
    > [!NOTE]
    >  Definicji typu ogólnego jest wyrażony jako `IEnumerable<>` korzystając `typeof` operatora w języku C# lub `IEnumerable(Of )` korzystając `GetType` operatora w języku Visual Basic.  
  
     Teraz można pobrać konstruktora `List<T>` przez wywołanie metody <xref:System.Type.GetConstructor%2A> w definicji typu ogólnego. Aby przekonwertować tego konstruktora odpowiedniego konstruktora `List<TFirst>`, Przekaż `List<TFirst>` i konstruktora z `List<T>` do statycznego <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> — metoda.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Utwórz typ i Zapisz plik.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Wywołanie metody. `ExampleMethod`nie jest rodzajowa, ale należy do typu jest ogólny, tak aby można było pobrać <xref:System.Reflection.MethodInfo> może być wywoływany jest niezbędne do utworzenia skonstruowanego typu z definicji typu dla `Sample`. Używa utworzony typ `Example` klasy, która spełnia ograniczenia na `TFirst` ponieważ jest typem referencyjnym i ma domyślny konstruktor bez parametrów i `ExampleDerived` klasy, która spełnia ograniczenia na `TSecond`. (Kod `ExampleDerived` można znaleźć w sekcji z przykładowym kodem.) Te dwa typy są przekazywane do <xref:System.Type.MakeGenericType%2A> do utworzenia skonstruowanego typu. <xref:System.Reflection.MethodInfo> Następnie są uzyskiwane przy użyciu <xref:System.Type.GetMethod%2A> metody.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Poniższy kod tworzy tablicę `Example` obiektów, umieszcza tablicy w tablicy typu <xref:System.Object> reprezentujących argumenty metody do wywołania i przekazuje je do <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> metody. Pierwszy argument funkcji <xref:System.Reflection.MethodBase.Invoke%2A> metoda jest odwołanie o wartości null, ponieważ metoda jest `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje klasę o nazwie `Sample`, wraz z klasy podstawowej i dwa interfejsy. Program definiuje dwa parametry typu ogólnego `Sample`, włączając w typie podstawowym. Parametrów typu są jedynym elementem, który sprawia, że typ jest rodzajowy. Powoduje wyświetlenie to poprzez wyświetlenie komunikatu testowego przed i po definicji parametrów typu.  
  
 Parametr typu `TSecond` służy do zaprezentowania ograniczenia klasy i interfejs, za pomocą klasy podstawowej i interfejsów, a parametr typu `TFirst` służy do zaprezentowania ograniczeń specjalnych.  
  
 Przykładowy kod definiuje pole i przy użyciu parametrów typu klasy, dla typu pola i dla parametru metody i zwracany typ metody.  
  
 Po `Sample` klasa została utworzona, jest wywoływana metoda.  
  
 Program zawiera metodę, która zawiera informacje dotyczące typu ogólnego i metody, która zawiera listę ograniczeń specjalnych w parametrze typu. Te metody są używane do wyświetlania informacji na temat gotowe `Sample` klasy.  
  
 Program zapisze Zakończono modułu na dysku jako `GenericEmitExample1.dll`, więc możesz otworzyć go z [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) i sprawdź, czy MSIL dla `Sample` klasy.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawów dodatkowe są wymagane.  
  
-   Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe. Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>  
 [Emituj za pomocą odbicia](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Emisja odbicia scenariuszy w zestawie dynamicznym](http://msdn.microsoft.com/library/e1cc6750-e20f-473b-bb4e-f43bc66aecce)
