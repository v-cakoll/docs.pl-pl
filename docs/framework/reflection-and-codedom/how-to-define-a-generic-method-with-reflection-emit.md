---
title: "Porady: definiowanie metody ogólnej przy użyciu emisji odbicia"
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
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic methods
- generics [.NET Framework], dynamic types
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f894d032527611c036e41fff783b31920c354778
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Porady: definiowanie metody ogólnej przy użyciu emisji odbicia
Pierwsza procedura pokazuje, jak utworzyć prostą metodę ogólnego z dwoma parametrami typu i sposób stosowania ograniczenia klasy, interfejsu, ograniczenia i ograniczeń specjalnych parametrów typu.  
  
 Druga procedura pokazuje, jak Emituj treść metody i jak używać parametrów typu metody ogólnej do tworzenia wystąpień typów ogólnych i ich metod wywołania.  
  
 Trzeci procedury przedstawiono sposób wywołania metody ogólnej.  
  
> [!IMPORTANT]
>  Metoda nie jest rodzajowa tak, ponieważ należy do typu ogólnego i używa parametrów typu tego typu. Metody jest rodzajowy, tylko wtedy, gdy ma własną listy parametrów typu. Metoda ogólna może występować w nierodzajowe typu, jak w poniższym przykładzie. Na przykład nierodzajowe metody dla typu ogólnego. zobacz [porady: Definiowanie typu ogólnego z emisja odbicia](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-method"></a>Aby zdefiniować Metoda ogólna  
  
1.  Przed rozpoczęciem, warto przyjrzeć się wygląd Metoda ogólna napisane przy użyciu języka wysokiego poziomu. Poniższy kod znajduje się w przykładowym kodzie w tym temacie wraz z wywołania metody ogólnej. Metoda ma dwa parametry typu `TInput` i `TOutput`, drugi z nich musi być typu odwołania (`class`), musi mieć konstruktora bez parametrów (`new`) i musi implementować `ICollection(Of TInput)` (`ICollection<TInput>` w języku C#). To ograniczenie interfejsu upewnia się, że <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metody można użyć do dodawania elementów do `TOutput` kolekcji, która tworzy metody. Metoda ma jeden formalny parametr `input`, który jest tablicą `TInput`. Ta metoda tworzy kolekcję typu `TOutput` i kopiuje elementy `input` do kolekcji.  
  
     [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
     [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]  
  
2.  Zdefiniuj zestawie dynamicznym i należy module dynamicznym zawierać typu metody ogólnej. W takim przypadku zestaw ma tylko jeden moduł o nazwie `DemoMethodBuilder1`, a nazwa modułu jest taka sama nazwa zestawu i rozszerzenia. W tym przykładzie zestaw jest zapisywany na dysku i również wykonywane, to <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> jest określona. Można użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zbadać DemoMethodBuilder1.dll i porównania go na język pośredni firmy Microsoft (MSIL) dla metody przedstawionym w kroku 1.  
  
     [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
     [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]  
  
3.  Zdefiniuj typ, którego Metoda ogólna należy. Typ nie ma być rodzajowy. Metoda ogólna może należeć do typu ogólnego lub nierodzajowe. W tym przykładzie typ to klasa, nie jest rodzajowa i nosi nazwę `DemoType`.  
  
     [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
     [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]  
  
4.  Definiowanie metody ogólnej. Jeśli typy parametrów formalnych Metoda ogólna są określane przez ogólnych parametrów typu metody ogólnej, użyj <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> przeciążenie metody w celu zdefiniowania metody. Parametry typu ogólnego metody nie zostały jeszcze zdefiniowane, więc nie można określić typy parametrów formalnych metody w wywołaniu <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>. W tym przykładzie metodę o nazwie `Factory`. Metoda jest publiczna i `static` (`Shared` w języku Visual Basic).  
  
     [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
     [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]  
  
5.  Zdefiniuj parametry typu ogólnego `DemoMethod` przez przekazanie tablica ciągów zawierająca nazwy parametrów w celu <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> metody. Dzięki temu ta metoda metody rodzajowej. Poniższy kod sprawia, że `Factory` Metoda ogólna z parametrami typu `TInput` i `TOutput`. Aby czytelność kodu, zmiennych o tych nazwach, są tworzone do przechowywania <xref:System.Reflection.Emit.GenericTypeParameterBuilder> obiekty reprezentujące dwa typy parametrów.  
  
     [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
     [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]  
  
6.  Opcjonalnie można dodać ograniczeń specjalnych do parametrów typu. Ograniczeń specjalnych są dodawane przy użyciu <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> metody. W tym przykładzie `TOutput` jest ograniczona, typu odwołania i ma konstruktora bez parametrów.  
  
     [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
     [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]  
  
7.  Opcjonalnie można dodać ograniczenia klasy i interfejs do parametrów typu. W tym przykładzie parametr typu `TOutput` jest ograniczona do typów, które implementują `ICollection(Of TInput)` (`ICollection<TInput>` w języku C#) interfejsu. Gwarantuje to, że <xref:System.Collections.Generic.ICollection%601.Add%2A> metody można użyć do dodawania elementów.  
  
     [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
     [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]  
  
8.  Zdefiniowanie parametrów formalnych metody, przy użyciu <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> metody. W tym przykładzie `Factory` metoda ma jeden parametr, tablicę `TInput`. Ten typ jest tworzony przez wywołanie metody <xref:System.Type.MakeArrayType%2A> metoda <xref:System.Reflection.Emit.GenericTypeParameterBuilder> reprezentujący `TInput`. Argument <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> jest tablicą <xref:System.Type> obiektów.  
  
     [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
     [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]  
  
9. Zdefiniuj typ zwracany przez metodę, przy użyciu <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> metody. W tym przykładzie wystąpienia `TOutput` jest zwracany.  
  
     [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
     [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]  
  
10. Emituj metody treści, przy użyciu <xref:System.Reflection.Emit.ILGenerator>. Aby uzyskać więcej informacji zobacz procedurę towarzyszący do emitowania treści metody.  
  
    > [!IMPORTANT]
    >  Emituj wywołania metod typów ogólnych i argumentów typu tych typów są parametry typu metody ogólnej, należy używać `static` <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>, i <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> metoda przeciąża z <xref:System.Reflection.Emit.TypeBuilder> klasa do Uzyskaj skonstruowane formularze metod. Procedury towarzyszące emitowanie treści metody pokazano to.  
  
11. Ukończ typ zawierający metody i Zapisz zestaw. Wywoływanie metody ogólnej procedury towarzyszące przedstawia dwa sposoby wywołania metody ukończone.  
  
     [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
     [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]  
  
<a name="procedureSection1"></a>   
### <a name="to-emit-the-method-body"></a>Aby emitować treści metody  
  
1.  Pobierz generator kodu i deklarować zmiennych lokalnych i etykiet. <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> Metoda służy do deklarowania zmiennych lokalnych. `Factory` Metoda ma cztery zmiennych lokalnych: `retVal` aby pomieścić nowy `TOutput` który jest zwracany przez metodę `ic` do przechowywania `TOutput` po jest rzutowane na `ICollection(Of TInput)` (`ICollection<TInput>` w języku C#), `input` do Przytrzymaj tablicy wejściowej z `TInput` obiektów, a `index` do iterowania po tablicy. Metoda ma również dwie etykiety, jedna, aby wprowadzić pętli (`enterLoop`) i jeden dla górnej pętli (`loopAgain`), zdefiniowany za pomocą <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> — metoda.  
  
     Pierwszą czynnością jest metoda jest pobranie jej argument <xref:System.Reflection.Emit.OpCodes.Ldarg_0> opcode i zapisz go w zmiennej lokalnej `input` przy użyciu <xref:System.Reflection.Emit.OpCodes.Stloc_S> opcode.  
  
     [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
     [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]  
  
2.  Emituj kod w celu utworzenia wystąpienia `TOutput`, za pomocą przeciążenia metody ogólnej <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody. Za pomocą tego przeciążenia wymaga określony typ ma konstruktora bez parametrów, czyli Przyczyna dodanie tego ograniczenia do `TOutput`. Utwórz skonstruowane Metoda ogólna przez przekazanie `TOutput` do <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Po emitowanie kodu, aby wywołać metodę, wyemitować kodu, zapisz go w zmiennej lokalnej `retVal` przy użyciu<xref:System.Reflection.Emit.OpCodes.Stloc_S>  
  
     [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
     [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]  
  
3.  Emituj kod można rzutować nowe `TOutput` do obiektu `ICollection(Of TInput)` i zapisz go w zmiennej lokalnej `ic`.  
  
     [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
     [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]  
  
4.  Pobierz <xref:System.Reflection.MethodInfo> reprezentujący <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metody. Metoda działa na `ICollection(Of TInput)` (`ICollection<TInput>` w języku C#), więc konieczne jest uzyskanie `Add` metody określonej w tym skonstruować typu. Nie można użyć <xref:System.Type.GetMethod%2A> metodę, aby uzyskać dostęp do tej <xref:System.Reflection.MethodInfo> bezpośrednio z `icollOfTInput`, ponieważ <xref:System.Type.GetMethod%2A> nie jest obsługiwana dla typu, który został skonstruowany przy <xref:System.Reflection.Emit.GenericTypeParameterBuilder>. Zamiast tego wywołać <xref:System.Type.GetMethod%2A> na `icoll`, który zawiera definicję typu ogólnego <xref:System.Collections.Generic.ICollection%601> interfejs generyczny. Następnie użyj <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` metodę, aby utworzyć <xref:System.Reflection.MethodInfo> skonstruowanego typu. Poniższy kod przedstawia to.  
  
     [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
     [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]  
  
5.  Emituj kod do zainicjowania `index` zmiennej przez ładowanie 32-bitową liczbę całkowitą 0 i przechowywanie ich w zmiennej. Emituj kod do gałęzi do etykiety `enterLoop`. Etykieta nie jeszcze została oznaczona, ponieważ znajduje się wewnątrz pętli. Kod dla pętli są emitowane w następnym kroku.  
  
     [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
     [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]  
  
6.  Emituj kodu dla pętli. Pierwszym krokiem jest oznaczenie górnej pętli, wywołując <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> z `loopAgain` etykiety. Branch — instrukcje używających etykieta zostanie teraz gałęzi w tym punkcie w kodzie. Następnym krokiem jest push `TOutput` obiektu rzutować `ICollection(Of TInput)`, na stosie. Nie jest wymagane natychmiast, ale musi być w pozycji dla wywołania `Add` metody. Dalej tablicy wejściowej spoczywa na stosie, a następnie `index` zmienną, która zawiera bieżący indeks w tablicy. <xref:System.Reflection.Emit.OpCodes.Ldelem> Kod operacji POP indeks i Tablica ze stosu i umieszcza elementu tablicy indeksowanej na stosie. Stos jest gotowy dla wywołania <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metodę, która będzie wyświetlana, kolekcji i nowego elementu ze stosu i dodaje element do kolekcji.  
  
     Zwiększa pozostałej części kodu w pętli indeks i testy, aby zobaczyć, czy Zakończenie pętli: indeks 32-bitową liczbę całkowitą 1 wypychana na stosie i dodany, pozostawiając Suma na stosie; Suma są przechowywane w `index`. <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A>wywoływana jest ustawiony jako punkt wejścia dla pętli tego punktu. Indeks został załadowany ponownie. Tablica wejściowa spoczywa na stosie, i <xref:System.Reflection.Emit.OpCodes.Ldlen> jest emitowany uzyskać jego długość. Indeks i długość są teraz na stosie, i <xref:System.Reflection.Emit.OpCodes.Clt> jest emitowany do porównania. Jeśli indeks jest mniejszy niż długość, <xref:System.Reflection.Emit.OpCodes.Brtrue_S> oddziałów z powrotem do początku pętli.  
  
     [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
     [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]  
  
7.  Emituj kod, aby wypychać `TOutput` obiektu na stosie i zwracany przez metodę. Zmienne lokalne `retVal` i `ic` zawierają odwołania do nowego `TOutput`; `ic` służy tylko do dostępu <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> metody.  
  
     [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
     [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]  
  
<a name="procedureSection2"></a>   
### <a name="to-invoke-the-generic-method"></a>Można wywołać metody ogólne  
  
1.  `Factory`jest ogólną definicją metody. Aby można było wywołać go, należy przypisać typów jego parametrów typu ogólnego. Użyj <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> metody w tym celu. Poniższy kod tworzy skonstruowane metody ogólnej, określając <xref:System.String> dla `TInput` i `List(Of String)` (`List<string>` w języku C#) dla `TOutput`i wyświetla reprezentację ciągu metody.  
  
     [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
     [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]  
  
2.  Aby wywołać metodę późnym wiązaniem, użyj <xref:System.Reflection.MethodBase.Invoke%2A> metody. Poniższy kod tworzy tablicę <xref:System.Object>, zawierające jako jej jedynym elementem tablicy ciągów i przekazuje ją jako listy argumentów dla metody ogólnej. Pierwszy parametr <xref:System.Reflection.MethodBase.Invoke%2A> jest odwołanie o wartości null, ponieważ metoda jest `static`. Wartość zwracana jest rzutowane na `List(Of String)`, i nie jest wyświetlany pierwszego elementu.  
  
     [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
     [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]  
  
3.  Aby wywołać metodę delegata, musi mieć delegata, który pasuje do podpisu skonstruowane metoda rodzajowa. Prosty sposób, w tym celu jest utworzyć to delegat generyczny. Poniższy kod tworzy wystąpienie Delegat ogólny `D` zdefiniowane w przykładowym kodzie za pomocą <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> przeciążenie metody i wywołuje delegata. Obiekty delegowane lepiej niż wywołania z późnym wiązaniem.  
  
     [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
     [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]  
  
4.  Metoda emitowany można skrót z programu, który odwołuje się do zestawu zapisane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy typu nierodzajowe `DemoType`, metodą rodzajową `Factory`. Ta metoda ma dwa parametry typu ogólnego, `TInput` Aby określić typ danych wejściowych i `TOutput` określenia typu danych wyjściowych. `TOutput` Parametr typu jest ograniczona do zaimplementowania `ICollection<TInput>` (`ICollection(Of TInput)` w języku Visual Basic), typu odwołania i mieć konstruktora bez parametrów.  
  
 Metoda ma jeden formalny parametr, który jest tablicą o `TInput`. Metoda zwraca wystąpienie klasy `TOutput` zawierający wszystkie elementy tablicy wejściowej. `TOutput`mogą być dowolnego typu kolekcja ogólna, który implementuje <xref:System.Collections.Generic.ICollection%601> interfejs generyczny.  
  
 Podczas wykonywania kodu zostanie zapisany jako DemoGenericMethod1.dll zestawu dynamicznego, a przy [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
> [!NOTE]
>  Dobrym sposobem Dowiedz się, jak można wyemitować kodu jest Napisz program Visual Basic, C# lub Visual C++, który wykonuje zadanie, które próbujesz Emituj i użyj dezasembler Sprawdź MSIL generowane przez kompilator.  
  
 Przykładowy kod zawiera kod źródłowy, który jest odpowiednikiem emitowany metody. Emitowany — metoda jest wywoływana z późnym wiązaniem i również przy użyciu Delegat ogólny zadeklarowany w przykładzie kodu.  
  
 [!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
 [!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawów dodatkowe są wymagane.  
  
-   Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe. Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Emit.MethodBuilder>  
 [Porady: Definiowanie typu ogólnego z odbiciem emisji](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)
