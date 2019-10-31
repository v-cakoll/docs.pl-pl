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
ms.openlocfilehash: b553fd2235c73cf879474dc4f44f958dddcb649c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130155"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Porady: definiowanie typu ogólnego przy użyciu emisji odbicia
W tym temacie pokazano, jak utworzyć prosty typ ogólny z dwoma parametrami typu, jak zastosować ograniczenia klas, ograniczenia interfejsu i ograniczenia specjalne do parametrów typu oraz jak tworzyć składowe, które używają parametrów typu klasy jako typów parametrów i typy zwracane.  
  
> [!IMPORTANT]
> Metoda nie jest typowa, ponieważ należy do typu ogólnego i używa parametrów typu tego typu. Metoda jest generyczna tylko wtedy, gdy ma własną listę parametrów typu. Większość metod na typach ogólnych nie jest ogólna, jak w tym przykładzie. Aby zapoznać się z przykładem emitowania metody ogólnej, zobacz [How to: define a metoda generyczna przy użyciu emisji odbicia](how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Aby zdefiniować typ ogólny  
  
1. Zdefiniuj zestaw dynamiczny o nazwie `GenericEmitExample1`. W tym przykładzie zestaw jest wykonywany i zapisywany na dysku, więc <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> jest określony.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. Zdefiniuj moduł dynamiczny. Zestaw składa się z modułów wykonywalnych. W przypadku zestawu jednomodułowego Nazwa modułu jest taka sama jak nazwa zestawu, a nazwa pliku to nazwa modułu i rozszerzenie.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. Zdefiniuj klasę. W tym przykładzie Klasa ma nazwę `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. Zdefiniuj parametry typu ogólnego `Sample`, przekazując tablicę ciągów zawierających nazwy parametrów do metody <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType>. Powoduje to, że Klasa jest typem ogólnym. Wartość zwracana jest tablicą <xref:System.Reflection.Emit.GenericTypeParameterBuilder> obiektów reprezentujących parametry typu, które mogą być używane w wyemitowanym kodzie.  
  
     W poniższym kodzie `Sample` jest typem ogólnym z parametrami typu `TFirst` i `TSecond`. Aby ułatwić odczytywanie kodu, każda <xref:System.Reflection.Emit.GenericTypeParameterBuilder> jest umieszczana w zmiennej o takiej samej nazwie jak parametr typu.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. Dodaj specjalne ograniczenia do parametrów typu. W tym przykładzie parametr typu `TFirst` jest ograniczony do typów, które mają konstruktory bez parametrów i do typów referencyjnych.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. Opcjonalnie dodaj ograniczenia klas i interfejsów do parametrów typu. W tym przykładzie parametr typu `TFirst` jest ograniczony do typów, które pochodzą od klasy bazowej reprezentowanej przez obiekt <xref:System.Type> zawarty w zmiennej `baseType`i który implementuje interfejsy, których typy są zawarte w zmiennych `interfaceA` i @no __t_4_ . Zobacz przykład kodu dla deklaracji i przypisania tych zmiennych.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. Zdefiniuj pole. W tym przykładzie typ pola jest określony przez parametr typu `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder> pochodzi od <xref:System.Type>, dlatego można użyć parametrów typu ogólnego wszędzie tam, gdzie można używać typu.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. Zdefiniuj metodę, która używa parametrów typu typu ogólnego. Należy zauważyć, że takie metody nie są ogólne, chyba że mają własne listy parametrów typu. Poniższy kod definiuje metodę `static` (`Shared` w Visual Basic), która pobiera tablicę `TFirst` i zwraca `List<TFirst>` (`List(Of TFirst)` w Visual Basic) zawierający wszystkie elementy tablicy. Aby zdefiniować tę metodę, konieczne jest utworzenie typu `List<TFirst>` przez wywołanie <xref:System.Type.MakeGenericType%2A> w definicji typu ogólnego, `List<T>`. (`T` jest pomijany podczas używania operatora `typeof` (`GetType` w Visual Basic) do pobrania definicji typu ogólnego.) Typ parametru jest tworzony przy użyciu metody <xref:System.Type.MakeArrayType%2A>.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Emituj treść metody. Treść metody składa się z trzech kodów operacji, które ładują tablicę wejściową do stosu, wywołują Konstruktor `List<TFirst>`, który pobiera `IEnumerable<TFirst>` (które wykonuje wszystkie czynności umieszczania elementów wejściowych na liście) i zwracają (pozostawiając nowy obiekt <xref:System.Collections.Generic.List%601> na stosie). Trudna część emitowania tego kodu uzyskuje Konstruktor.  
  
     Metoda <xref:System.Type.GetConstructor%2A> nie jest obsługiwana w <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, więc nie można uzyskać konstruktora `List<TFirst>` bezpośrednio. Najpierw należy uzyskać konstruktora definicji typu ogólnego `List<T>` a następnie wywołać metodę, która konwertuje ją na odpowiedni Konstruktor `List<TFirst>`.  
  
     Konstruktor używany do tego przykładu kodu przyjmuje `IEnumerable<T>`. Należy jednak pamiętać, że nie jest to definicja typu ogólnego <xref:System.Collections.Generic.IEnumerable%601> ogólnego interfejsu; Zamiast tego parametr typu `T` od `List<T>` musi zostać zastąpiony dla parametru typu `T` `IEnumerable<T>`. (Dzieje się to tylko mylące, ponieważ oba typy mają parametry typu o nazwie `T`. Dlatego ten przykład kodu używa nazw `TFirst` i `TSecond`.) Aby uzyskać typ argumentu konstruktora, należy rozpocząć od definicji typu ogólnego `IEnumerable<T>` i wywołać <xref:System.Type.MakeGenericType%2A> z pierwszym parametrem typu ogólnego `List<T>`. Lista argumentów konstruktora musi być przenoszona jako tablica, a w tym przypadku tylko jeden argument.  
  
    > [!NOTE]
    > Definicja typu ogólnego jest wyrażona jako `IEnumerable<>` w przypadku używania operatora `typeof` w C#, lub `IEnumerable(Of )` w przypadku używania operatora `GetType` w Visual Basic.  
  
     Teraz można uzyskać konstruktora `List<T>`, wywołując <xref:System.Type.GetConstructor%2A> w definicji typu ogólnego. Aby przekonwertować ten Konstruktor na odpowiedni Konstruktor `List<TFirst>`, należy przekazać `List<TFirst>` i konstruktora z `List<T>` do statycznej metody <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType>.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Utwórz typ i Zapisz plik.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Wywołaj metodę. `ExampleMethod` nie jest ogólny, ale typ, do którego należy, jest rodzajowy, więc w celu uzyskania <xref:System.Reflection.MethodInfo>, który może zostać wywołany, jest konieczne do utworzenia typu złożonego z definicji typu dla `Sample`. Typ skonstruowany używa klasy `Example`, która spełnia ograniczenia dotyczące `TFirst`, ponieważ jest typem referencyjnym i ma domyślny konstruktor bez parametrów, a Klasa `ExampleDerived`, która spełnia ograniczenia na `TSecond`. (Kod `ExampleDerived` można znaleźć w sekcji przykład kodu). Te dwa typy są przesyłane do <xref:System.Type.MakeGenericType%2A>, aby utworzyć typ skonstruowany. Następnie <xref:System.Reflection.MethodInfo> jest uzyskiwany przy użyciu metody <xref:System.Type.GetMethod%2A>.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Poniższy kod tworzy tablicę obiektów `Example`, umieszcza tę tablicę w tablicy typu <xref:System.Object> reprezentującą argumenty metody do wywołania i przekazuje je do metody <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29>. Pierwszym argumentem metody <xref:System.Reflection.MethodBase.Invoke%2A> jest odwołanie o wartości null, ponieważ metoda jest `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje klasę o nazwie `Sample`, wraz z klasą bazową i dwoma interfejsami. Program definiuje dwa parametry typu ogólnego dla `Sample`, przełączając je do typu ogólnego. Parametry typu są jedynym elementem, który tworzy rodzajowy typ. Program pokazuje to poprzez wyświetlenie komunikatu testowego przed i po definicji parametrów typu.  
  
 Parametr typu `TSecond` jest używany do zademonstrowania ograniczeń klas i interfejsów, przy użyciu klasy bazowej i interfejsów, a parametr typu `TFirst` służy do zademonstrowania specjalnych ograniczeń.  
  
 Przykładowy kod definiuje pole i metodę przy użyciu parametrów typu klasy dla typu pola oraz parametrów i zwracanego typu metody.  
  
 Po utworzeniu klasy `Sample` Metoda jest wywoływana.  
  
 Program zawiera metodę, która wyświetla informacje o typie ogólnym i metodę, która wyświetla specjalne ograniczenia w parametrze typu. Te metody są używane do wyświetlania informacji o zakończeniu klasy `Sample`.  
  
 Program zapisuje gotowy moduł na dysku jako `GenericEmitExample1.dll`, więc można go otworzyć za pomocą [Ildasm. exe (Il dezasembler)](../tools/ildasm-exe-il-disassembler.md) i przejrzeć MSIL dla klasy `Sample`.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- [Używanie emisji odbicia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Scenariusze dynamicznego wyemituj z odbiciem](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))
