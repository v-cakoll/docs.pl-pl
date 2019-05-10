---
title: 'Instrukcje: Definiowanie metody ogólnej przy użyciu emisji odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic methods
- generics [.NET Framework], dynamic types
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: daebcf210dfa484c49f52635bb5c3c8f74c8a88a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591725"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Instrukcje: Definiowanie metody ogólnej przy użyciu emisji odbicia
Pierwsza procedura pokazuje, jak utworzyć proste metody ogólnej z dwoma parametrami typu, a także jak zastosować ograniczenia klasy, interfejsu, ograniczenia i ograniczenia specjalne do parametrów typu.  
  
 Druga procedura pokazuje, jak do wysyłania treści metody oraz jak używać parametrów typu ogólnego metody do tworzenia wystąpień typów ogólnych i wywołania ich metod.  
  
 Trzeci procedura przedstawia sposób wywołania metody rodzajowej.  
  
> [!IMPORTANT]
>  Metoda nie jest ogólna tylko w przypadku, ponieważ należy do typu ogólnego i używa parametrów typu tego typu. Metoda jest ogólna tylko wtedy, gdy ma ona własną lista parametrów typu. Metody ogólnej może znajdować się w danym typie nierodzajowych, jak w poniższym przykładzie. Na przykład nierodzajowymi metoda w typie rodzajowym zobacz [jak: Definiowanie typu ogólnego przy użyciu odbicia emitować](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-method"></a>Aby zdefiniować metody ogólnej  
  
1. Przed rozpoczęciem warto przyjrzyj wyświetlania metody ogólnej napisane przy użyciu języka wysokiego poziomu. Poniższy kod znajduje się w przykładowym kodzie, w tym temacie, wraz z kodem do wywoływania metody rodzajowej. Metoda ma dwa parametry typu `TInput` i `TOutput`, drugi z nich musi być typem referencyjnym (`class`), musi mieć konstruktora bez parametrów (`new`) i musi implementować `ICollection(Of TInput)` (`ICollection<TInput>` w C#). To ograniczenie interfejs zapewnia, że <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metoda może służyć do dodawania elementów do `TOutput` kolekcji, która tworzy metodę. Metoda ma jeden parametr formalny, `input`, który jest tablicą `TInput`. Ta metoda tworzy kolekcję typu `TOutput` i kopiuje elementy ze `input` do kolekcji.  
  
     [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
     [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]  
  
2. Definiowanie zestawu dynamicznego i zawierać typu metody ogólnej modułu dynamicznego należy do. W tym przypadku zestaw ma tylko jeden moduł, o nazwie `DemoMethodBuilder1`, i nazwę modułu jest taka sama jak nazwa zestawu i rozszerzenia. W tym przykładzie zestawu jest zapisywany na dysku i również wykonała, więc <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> jest określony. Możesz użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zbadać DemoMethodBuilder1.dll i porównać go do języka Microsoft intermediate language (MSIL) metody przedstawionym w kroku 1.  
  
     [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
     [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]  
  
3. Zdefiniuj typ, której metody rodzajowej. Typ ma być ogólna. Metody ogólne mogą należeć do typu ogólnego lub nierodzajowymi. W tym przykładzie typ jest klasą, nie jest ogólna i nosi nazwę `DemoType`.  
  
     [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
     [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]  
  
4. Definiowanie metody ogólnej. Jeśli nie określono typy parametrów formalnych metody ogólnej przez parametrów typu ogólnego dla metody rodzajowej, użyj <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> przeciążenia metody, aby zdefiniować metodę. Parametry typu ogólnego metody nie zostały jeszcze zdefiniowane, więc nie można określić typy parametrów formalnych metody w wywołaniu <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>. W tym przykładzie nosi nazwę metody `Factory`. Ta metoda jest publiczny i `static` (`Shared` w języku Visual Basic).  
  
     [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
     [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]  
  
5. Definiowanie parametrów typu ogólnego `DemoMethod` , przekazując tablicę ciągów, które zawierają nazwy parametrów w celu <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> metody. To sprawia, że metoda metody rodzajowej. Poniższy kod powoduje, że `Factory` metody ogólnej z parametrami typu `TInput` i `TOutput`. Aby kod była łatwiejsza do odczytania, zmiennych o tych nazwach są tworzone na potrzeby przechowywania <xref:System.Reflection.Emit.GenericTypeParameterBuilder> obiekty reprezentujące dwa typy parametrów.  
  
     [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
     [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]  
  
6. Opcjonalnie dodaj specjalne ograniczenia parametrów typu. Specjalne ograniczenia są dodawane przy użyciu <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> metody. W tym przykładzie `TOutput` jest ograniczony do jako typów referencyjnych i ma konstruktora bez parametrów.  
  
     [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
     [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]  
  
7. Opcjonalnie można dodać ograniczenia klasy i interfejs do parametrów typu. W tym przykładzie parametr typu `TOutput` jest ograniczony do typów, które implementują `ICollection(Of TInput)` (`ICollection<TInput>` w C#) interfejsu. Gwarantuje to, że <xref:System.Collections.Generic.ICollection%601.Add%2A> metoda może służyć do dodawania elementów.  
  
     [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
     [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]  
  
8. Definiowanie parametrów formalnych metody, przy użyciu <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> metody. W tym przykładzie `Factory` metoda ma jeden parametr, tablicę `TInput`. Ten typ jest tworzony przez wywołanie metody <xref:System.Type.MakeArrayType%2A> metody <xref:System.Reflection.Emit.GenericTypeParameterBuilder> reprezentujący `TInput`. Argument <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> jest tablicą <xref:System.Type> obiektów.  
  
     [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
     [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]  
  
9. Zdefiniuj typ zwracany przez metodę, przy użyciu <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> metody. W tym przykładzie wystąpienie `TOutput` jest zwracana.  
  
     [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
     [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]  
  
10. Emituj metody treści, za pomocą <xref:System.Reflection.Emit.ILGenerator>. Aby uzyskać szczegółowe informacje Zobacz towarzyszący procedurę do emitowania treści metody.  
  
    > [!IMPORTANT]
    >  Emituj wywołania metod typów ogólnych i argumenty typu z tych typów są parametry typu metody ogólnej, należy użyć `static` <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>, i <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> przeciążenia metody <xref:System.Reflection.Emit.TypeBuilder> klasy Uzyskaj skonstruowany rodzaje metod. Towarzyszący procedury do emitowania treści metody pokazuje to.  
  
11. Typ, który zawiera metodę ukończenia, a następnie Zapisz zestaw. Towarzyszący procedury do wywoływania metody rodzajowej przedstawia dwa sposoby wywołania metody ukończone.  
  
     [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
     [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]  
  
<a name="procedureSection1"></a>   
### <a name="to-emit-the-method-body"></a>Do wysyłania treści metody  
  
1. Uzyskaj generatora kodu i zadeklarować zmienne lokalne i etykiety. <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> Metoda służy do deklarowania zmiennych lokalnych. `Factory` Metoda ma cztery zmiennych lokalnych: `retVal` do przechowywania nowej `TOutput` zwracanym przez metodę, `ic` do przechowywania `TOutput` kiedy jest rzutowany na `ICollection(Of TInput)` (`ICollection<TInput>` w C#), `input`do przechowywania tablicy wejściowej z `TInput` obiekty, i `index` można wykonać iterację tablicy. Metoda ma również dwie etykiety do wprowadź pętli (`enterLoop`) i jeden dla góry pętli (`loopAgain`) zdefiniowaną za pomocą <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> metody.  
  
     Pierwszą rzeczą, metoda jest pobranie jej argument <xref:System.Reflection.Emit.OpCodes.Ldarg_0> opcode i zapisz go w zmiennej lokalnej `input` przy użyciu <xref:System.Reflection.Emit.OpCodes.Stloc_S> opcode.  
  
     [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
     [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]  
  
2. Emituj kod, aby utworzyć wystąpienie `TOutput`, za pomocą przeciążenia metody ogólnej <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody. Korzystanie z tego przeciążenia wymaga określonego typu ma konstruktora bez parametrów, która jest dodawana takiego ograniczenia do `TOutput`. Utwórz skonstruowany metody rodzajowej, przekazując `TOutput` do <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Po emitowanie kodu w celu wywołania metody, emitują kod, aby zapisać ją w zmiennej lokalnej `retVal` przy użyciu <xref:System.Reflection.Emit.OpCodes.Stloc_S>  
  
     [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
     [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]  
  
3. Emitują kod, aby rzutować nowy `TOutput` obiekt `ICollection(Of TInput)` i zapisz go w zmiennej lokalnej `ic`.  
  
     [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
     [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]  
  
4. Pobierz <xref:System.Reflection.MethodInfo> reprezentujący <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metody. Metoda działa na `ICollection(Of TInput)` (`ICollection<TInput>` w C#), co jest niezbędne do doprowadzenia `Add` metody określonej w tym skonstruowany typ. Nie można użyć <xref:System.Type.GetMethod%2A> metodę, aby uzyskać dostęp do tej <xref:System.Reflection.MethodInfo> bezpośrednio z `icollOfTInput`, ponieważ <xref:System.Type.GetMethod%2A> nie jest obsługiwana dla typu, który został skonstruowany przy użyciu <xref:System.Reflection.Emit.GenericTypeParameterBuilder>. Zamiast tego należy wywołać <xref:System.Type.GetMethod%2A> na `icoll`, który zawiera definicję typu ogólnego <xref:System.Collections.Generic.ICollection%601> interfejs generyczny. Następnie użyj <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` metody do tworzenia <xref:System.Reflection.MethodInfo> skonstruowanego typu. Poniższy kod przedstawia to.  
  
     [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
     [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]  
  
5. Emituj kod, aby zainicjować `index` zmiennej, ładując 32-bitowej liczby całkowitej 0 i zapisanie go w zmiennej. Emitowanie kodu do gałęzi do etykiety `enterLoop`. Ta etykieta nie jeszcze została oznaczona, ponieważ znajduje się wewnątrz pętli. Kod dla pętli jest emitowane w następnym kroku.  
  
     [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
     [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]  
  
6. Wyemitować kodu dla pętli. Pierwszym krokiem jest do oznaczania początku pętli, wywołując <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> z `loopAgain` etykiety. Branch — instrukcje używające etykiety będą teraz gałąź do tego momentu w kodzie. Następnym krokiem jest wypychania `TOutput` obiektu rzutować `ICollection(Of TInput)`, na stosie. Nie jest wymagane natychmiast, ale musi znajdować się w miejscu do wywoływania `Add` metody. Dalej Tablica wejściowa jest wypychane na stosie, a następnie `index` zmienną, która zawiera bieżący indeks do tablicy. <xref:System.Reflection.Emit.OpCodes.Ldelem> Opcode POP, indeksu i tablicy ze stosu i wypycha elementu tablicy indeksowanej na stosie. Stos jest teraz gotowa do wywołania <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metody, która pojawia się kolekcja i nowy element ze stosu i dodaje element do kolekcji.  
  
     Pozostała część kodu w pętli zwiększa indeks i testy, aby zobaczyć, czy pętla została zakończona: Indeks i 32-bitowa liczba całkowita 1 są wypychane na stosie i dodawane, pozostawiając Suma na stosie; Suma jest przechowywany w `index`. <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> jest wywoływana, aby ustawić ten punkt jako punkt wejścia dla pętli. Indeks jest ładowany ponownie. Tablica wejściowa jest wypychane na stos, a <xref:System.Reflection.Emit.OpCodes.Ldlen> jest emitowane, aby uzyskać jego długość. Indeks i długość są teraz w stosie, i <xref:System.Reflection.Emit.OpCodes.Clt> jest emitowany do porównania. Jeśli indeks jest mniejsza niż długość <xref:System.Reflection.Emit.OpCodes.Brtrue_S> gałęzi z powrotem do początku pętli.  
  
     [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
     [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]  
  
7. Emituj kod służący do wypychania `TOutput` obiektów na stosie i zwraca z metody. Zmienne lokalne `retVal` i `ic` zawierają odwołania do nowego `TOutput`; `ic` służy jedynie do access <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metody.  
  
     [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
     [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]  
  
<a name="procedureSection2"></a>   
### <a name="to-invoke-the-generic-method"></a>Do wywołania metody ogólnej  
  
1. `Factory` jest definicją metody rodzajowej. Aby można było ją wywołać, należy przypisać typów, do jego parametrów typu rodzajowego. Użyj <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> metodę, aby to zrobić. Poniższy kod tworzy skonstruowany metody rodzajowej, określając <xref:System.String> dla `TInput` i `List(Of String)` (`List<string>` w C#) dla `TOutput`i wyświetla reprezentację ciągu metody.  
  
     [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
     [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]  
  
2. Aby wywołać metody z późnym wiązaniem, należy użyć <xref:System.Reflection.MethodBase.Invoke%2A> metody. Poniższy kod tworzy tablicę <xref:System.Object>, zawierający jako jego jedynym elementem tablicę ciągów i przekazuje ją jako lista argumentów dla metody rodzajowej. Pierwszy parametr <xref:System.Reflection.MethodBase.Invoke%2A> jest odwołanie o wartości null, ponieważ ta metoda jest `static`. Wartość zwracana jest rzutowany na `List(Of String)`, a jej pierwszy element będzie wyświetlany.  
  
     [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
     [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]  
  
3. Aby wywołać metodę delegata, konieczne jest posiadanie delegat, który pasuje do podpisu skonstruowanego metody rodzajowej. Prosty sposób, w tym celu jest do utworzenia delegata ogólnego. Poniższy kod tworzy wystąpienie delegata ogólnego `D` zdefiniowane w przykładowym kodzie za pomocą <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> przeciążenie metody i wywołuje delegata. Delegaty mają lepszą wydajność niż wywołania późnego wiązania.  
  
     [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
     [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]  
  
4. Metoda emitowany mogą być również wywoływane z programu, który odwołuje się do zestawu zapisane.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy typ nierodzajowych, `DemoType`, za pomocą metody rodzajowej, `Factory`. Ta metoda ma dwa parametry typu ogólnego, `TInput` określenia typu danych wejściowych i `TOutput` określenia typu danych wyjściowych. `TOutput` Parametr typu jest ograniczony do zaimplementowania `ICollection<TInput>` (`ICollection(Of TInput)` w języku Visual Basic), typ odwołania i ma konstruktora bez parametrów.  
  
 Metoda ma jeden parametr formalny, który jest tablicą o `TInput`. Metoda ta zwraca wystąpienie `TOutput` zawierający wszystkie elementy tablicy wejściowej. `TOutput` mogą być dowolnego typu kolekcji generycznej, która implementuje <xref:System.Collections.Generic.ICollection%601> interfejs generyczny.  
  
 Gdy kod jest wykonywany, jest zapisywany jako DemoGenericMethod1.dll zestawu dynamicznego i można zbadać za pomocą [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
> [!NOTE]
>  Dobrym sposobem na informacje o sposobie emitują kod jest napisanie języka Visual Basic, C#, lub w programie Visual C++, który wykonuje to zadanie, które próbujesz emitują i użyj dezasembler, aby sprawdzić MSIL wytworzone przez kompilator.  
  
 Przykład kodu zawiera kod źródłowy, który jest odpowiednikiem emitowany metody. Emitowany metoda jest wywoływana z późnym wiązaniem, a także za pomocą delegata ogólnego zadeklarowana w przykładzie kodu.  
  
 [!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
 [!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Zawiera kod języka C# `using` instrukcji (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
- Nie odwołania do zestawu dodatkowe są wymagane.  
  
- Skompilować kod w wierszu polecenia przy użyciu csc.exe i vbc.exe, cl.exe. Aby skompilować kod w programie Visual Studio, umieść go w szablonie projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Emit.MethodBuilder>
- [Instrukcje: Definiowanie typu ogólnego przy użyciu odbicia emisji](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)
