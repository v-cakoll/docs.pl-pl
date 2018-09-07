---
title: 'Porady: definiowanie typu ogólnego przy użyciu emisji odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32e06790ffebe49c7917ba4fc7344f86f7a49762
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085256"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Porady: definiowanie typu ogólnego przy użyciu emisji odbicia
W tym temacie pokazano, jak utworzyć prosty typ ogólny z dwoma parametrami typu, jak zastosować ograniczenia klasy, interfejsu, ograniczenia i ograniczenia specjalne do parametrów typu oraz sposobu tworzenia elementów członkowskich, które używają parametrów typu klasy jako typy parametrów i zwracanych typów.  
  
> [!IMPORTANT]
>  Metoda nie jest ogólna tylko w przypadku, ponieważ należy do typu ogólnego i używa parametrów typu tego typu. Metoda jest ogólna tylko wtedy, gdy ma ona własną lista parametrów typu. Większość metod w typach ogólnych nie są ogólny, jak w poniższym przykładzie. Aby uzyskać przykład emitowania metody rodzajowej, zobacz [porady: definiowanie metody ogólnej przy użyciu emisji odbicia](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Aby zdefiniować typ ogólny  
  
1.  Definiowanie zestawu dynamicznego o nazwie `GenericEmitExample1`. W tym przykładzie zestawu jest wykonywane i zapisywane na dysku, dlatego <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> jest określony.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  Definiowanie modułu dynamicznego. Zestaw składa się modułów wykonywalnych. Dla zestawu pojedynczego modułów Nazwa modułu jest taka sama jak nazwa zestawu i nazwa pliku jest nazwa modułu, plus rozszerzenie.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  Zdefiniuj klasę. W tym przykładzie klasę o nazwie `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  Definiowanie parametrów typu ogólnego `Sample` , przekazując tablicę ciągów, które zawierają nazwy parametrów w celu <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> metody. To sprawia, że klasy typu ogólnego. Wartość zwracana jest tablicą <xref:System.Reflection.Emit.GenericTypeParameterBuilder> obiekty reprezentujące parametrami typu, które mogą być używane w emitowany kod.  
  
     W poniższym kodzie `Sample` staje się typem ogólnym z parametrami typu `TFirst` i `TSecond`. Aby ułatwić interpretowanie każdy kod <xref:System.Reflection.Emit.GenericTypeParameterBuilder> jest umieszczana w zmiennej z taką samą nazwę jak parametr typu.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  Dodaj specjalne ograniczenia parametrów typu. W tym przykładzie parametr typu `TFirst` jest ograniczony do typów, które mają konstruktorów bez parametrów i na typy odwołań.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  Opcjonalnie można dodać ograniczenia klasy i interfejs do parametrów typu. W tym przykładzie parametr typu `TFirst` jest ograniczony do typów wyprowadzonych z klasy bazowej, reprezentowane przez <xref:System.Type> obiektów znajdujących się w zmiennej `baseType`, i implementują interfejsy, których typy są zawarte w zmiennych `interfaceA` i `interfaceB`. Zobacz przykład kodu dla deklarację i przypisanie tych zmiennych.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  Zdefiniuj pola. W tym przykładzie typ pola jest określony przez parametr typu `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder> pochodzi od klasy <xref:System.Type>, aby można było używać parametrów typu ogólnego, gdziekolwiek typ może być używany.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  Należy zdefiniować metodę, która używa parametrów typu ogólnego typu. Należy pamiętać, że takie metody nie są rodzajowe, chyba że mają swoje własne listy parametrów typu. Poniższy kod definiuje `static` — metoda (`Shared` w języku Visual Basic), przyjmuje tablicę `TFirst` i zwraca `List<TFirst>` (`List(Of TFirst)` w języku Visual Basic) zawierający wszystkie elementy tablicy. Aby zdefiniować tę metodę, jest to konieczne utworzyć typ `List<TFirst>` przez wywołanie metody <xref:System.Type.MakeGenericType%2A> w definicji typu ogólnego `List<T>`. ( `T` Zostanie pominięty, gdy używasz `typeof` — operator (`GetType` w języku Visual Basic) można pobrać definicji typu ogólnego.) Typ parametru jest tworzona przy użyciu <xref:System.Type.MakeArrayType%2A> metody.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Emituj treści metody. Treść metody składa się z trzech rozkazów, które ładują tablicy wejściowej na stosie, wywołaj `List<TFirst>` konstruktora przyjmującego `IEnumerable<TFirst>` (który wykonuje całą pracę, umieszczając elementów wejściowych na listę) i zwróć (pozostawiając nowy <xref:System.Collections.Generic.List%601> obiektu na stosie). Trudna część emitowania ten kod będzie niedługo konstruktora.  
  
     <xref:System.Type.GetConstructor%2A> Metoda nie jest obsługiwana na <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, więc nie jest możliwe uzyskanie konstruktora `List<TFirst>` bezpośrednio. Najpierw należy go pobrać konstruktora definicji typu ogólnego `List<T>` a następnie wywołać metodę, która konwertuje go do odpowiedniego konstruktora `List<TFirst>`.  
  
     Konstruktor używany dla tego przykładu kodu przyjmuje `IEnumerable<T>`. Należy jednak pamiętać, że nie jest definicja typu ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejs ogólny; zamiast tego parametru typu `T` z `List<T>` musi podstawiane za parametr typu `T` z `IEnumerable<T>`. (Zajmuje to nieco mylące tylko w przypadku, ponieważ oba typy ma parametry typu o nazwie `T`. That is, dlaczego ten przykład kodu używa nazwy `TFirst` i `TSecond`.) Aby uzyskać typ argumentu konstruktora, rozpoczynać się definicji typu ogólnego `IEnumerable<T>` i wywołać <xref:System.Type.MakeGenericType%2A> z pierwszym parametrem typu ogólnego `List<T>`. Lista argumentów konstruktora musi zostać przekazany jako tablicę z tylko jednym argumentem w tym przypadku.  
  
    > [!NOTE]
    >  Definicja typu ogólnego jest wyrażona jako `IEnumerable<>` zastosowania `typeof` operatora w języku C# lub `IEnumerable(Of )` zastosowania `GetType` operatora w języku Visual Basic.  
  
     Teraz można pobrać konstruktora z `List<T>` przez wywołanie metody <xref:System.Type.GetConstructor%2A> w definicji typu ogólnego. Aby przekonwertować tego konstruktora odpowiedniego konstruktora `List<TFirst>`, przekazać `List<TFirst>` i konstruktora z `List<T>` statycznej <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> metody.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Tworzenie typu, a następnie zapisz plik.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Wywołanie metody. `ExampleMethod` nie jest ogólna, ale ogólny, dlatego w celu uzyskania typu należy do <xref:System.Reflection.MethodInfo> może być wywoływany jest niezbędne do utworzenia skonstruowanego typu w definicji typu dla `Sample`. Skonstruowany typ używa `Example` klasy, która spełnia ograniczenia na `TFirst` ponieważ jest typem odwołania, a ma domyślny konstruktor bez parametrów i `ExampleDerived` klasę, która spełnia ograniczenia na `TSecond`. (Kod `ExampleDerived` można znaleźć w sekcji przykładu kodu.) Te dwa typy są przekazywane do <xref:System.Type.MakeGenericType%2A> w celu utworzenia skonstruowanego typu. <xref:System.Reflection.MethodInfo> Następnie uzyskuje się za pomocą <xref:System.Type.GetMethod%2A> metody.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Poniższy kod tworzy tablicę `Example` obiektów, umieszcza tę tablicę w tablicy typu <xref:System.Object> reprezentujący argumenty metody do wywołania i przekazuje je do <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> metody. Pierwszy argument <xref:System.Reflection.MethodBase.Invoke%2A> metoda jest odwołanie o wartości null, ponieważ ta metoda jest `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje klasę o nazwie `Sample`, wraz z klasy bazowej i dwa interfejsy. Program definiuje dwa parametry typu ogólnego dla `Sample`, włączając je w typie podstawowym. Parametry typu są jedynym elementem, który sprawia, że typ ogólny. Program pokazuje to poprzez wyświetlenie komunikatu testowego przed i po definicji parametrów typu.  
  
 Parametr typu `TSecond` jest używany do przedstawiania ograniczenia klasy i interfejs, za pomocą klasy bazowej i interfejsów, a parametr typu `TFirst` jest używany do przedstawiania ograniczeń specjalnych.  
  
 Przykładowy kod definiuje pola i metody za pomocą parametrów typu klasy, dla typu pola, a dla parametru i zwracany typ metody.  
  
 Po `Sample` klasa została utworzona, metoda jest wywoływana.  
  
 Program obejmuje metodę, która wyświetla informacje dotyczące typu ogólnego i metody, która zawiera specjalne ograniczenia dla parametru typu. Te metody są używane do wyświetlania informacji na temat gotowe `Sample` klasy.  
  
 Program zapisze Zakończono modułu na dysku jako `GenericEmitExample1.dll`, dzięki czemu można je otworzyć z [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) i sprawdzić MSIL dla `Sample` klasy.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod języka C# `using` instrukcji (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawu dodatkowe są wymagane.  
  
-   Skompilować kod w wierszu polecenia przy użyciu csc.exe i vbc.exe, cl.exe. Aby skompilować kod w programie Visual Studio, umieść go w szablonie projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>  
 [Używanie emisji odbicia](https://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Scenariusze zestawów dynamicznych emisji odbicia](https://msdn.microsoft.com/library/e1cc6750-e20f-473b-bb4e-f43bc66aecce)
