---
title: 'Porady: definiowanie i wykonywanie metod dynamicznych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
ms.openlocfilehash: 7da9d0bea755b90f73077fcd56558ed66a80e2eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130150"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Porady: definiowanie i wykonywanie metod dynamicznych
W poniższych procedurach pokazano, jak zdefiniować i wykonać prostą metodę dynamiczną oraz metodę dynamiczną powiązaną z wystąpieniem klasy. Aby uzyskać więcej informacji na temat metod dynamicznych, <xref:System.Reflection.Emit.DynamicMethod> zobacz [scenariusze metod dynamicznych emisji klasy i odbicia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Aby zdefiniować i wykonać metodę dynamiczną  
  
1. Zadeklaruj typ delegata, aby wykonać metodę. Rozważ użycie delegata ogólnego w celu zminimalizowania liczby typów delegatów, które należy zadeklarować. Poniższy kod deklaruje dwa typy delegatów, których można użyć dla `SquareIt` metody, a jeden z nich jest ogólny.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. Utwórz tablicę, która określa typy parametrów dla metody dynamicznej. W tym przykładzie jedynym parametrem jest `int` (`Integer` w Visual Basic), więc tablica ma tylko jeden element.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. Utwórz <xref:System.Reflection.Emit.DynamicMethod>. W tym przykładzie metoda ma nazwę `SquareIt`.  
  
    > [!NOTE]
    > Nie trzeba podawać nazw metod dynamicznych i nie mogą one być wywoływane przez nazwę. Wiele metod dynamicznych może mieć taką samą nazwę. Jednak nazwa pojawia się na stosach wywołań i może być przydatna do debugowania.  
  
     Typ wartości zwracanej jest określony jako `long`. Metoda jest skojarzona z modułem zawierającym `Example` klasę, która zawiera przykładowy kod. Można określić dowolny załadowany moduł. Metoda dynamiczna działa jak metoda na poziomie `static` modułu (`Shared` w Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. Emituj treść metody. W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do emitowania języka pośredniego firmy Microsoft (MSIL). Alternatywnie, <xref:System.Reflection.Emit.DynamicILInfo> obiekt może być używany w połączeniu z niezarządzanymi generatorami kodu w celu emitowania treści <xref:System.Reflection.Emit.DynamicMethod>metody dla.  
  
     MSIL w tym przykładzie ładuje argument, który jest `int`, na stosie, konwertuje go na `long`, duplikuje `long`i Mnoży dwie liczby. Spowoduje to pozostawienie kwadratowego wyniku na stosie, a wszystkie metody należy zwrócić.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. Utwórz wystąpienie delegata (zadeklarowane w kroku 1) reprezentujące metodę dynamiczną, wywołując <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metodę. Utworzenie delegata kończy metodę, a wszelkie dalsze próby zmiany metody — na przykład dodanie więcej MSIL — jest ignorowane. Poniższy kod tworzy delegata i wywołuje go za pomocą delegata ogólnego.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Aby zdefiniować i wykonać metodę dynamiczną, która jest powiązana z obiektem  
  
1. Zadeklaruj typ delegata, aby wykonać metodę. Rozważ użycie delegata ogólnego w celu zminimalizowania liczby typów delegatów, które należy zadeklarować. Poniższy kod deklaruje ogólny typ delegata, który może służyć do wykonywania dowolnej metody z jednym parametrem i wartością zwracaną, lub metodą z dwoma parametrami i wartością zwracaną, jeśli delegat jest powiązany z obiektem.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. Utwórz tablicę, która określa typy parametrów dla metody dynamicznej. Jeśli delegat reprezentujący metodę ma być powiązany z obiektem, pierwszy parametr musi być zgodny z typem, z którym jest powiązany delegat. W tym przykładzie istnieją dwa parametry typu `Example` i typu `int` (`Integer` w Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. Utwórz <xref:System.Reflection.Emit.DynamicMethod>. W tym przykładzie metoda nie ma nazwy. Typ wartości zwracanej jest określony jako `int` (`Integer` w Visual Basic). Metoda ma dostęp do prywatnych i chronionych składowych `Example` klasy.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. Emituj treść metody. W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do emitowania języka pośredniego firmy Microsoft (MSIL). Alternatywnie, <xref:System.Reflection.Emit.DynamicILInfo> obiekt może być używany w połączeniu z niezarządzanymi generatorami kodu w celu emitowania treści <xref:System.Reflection.Emit.DynamicMethod>metody dla.  
  
     MSIL w tym przykładzie ładuje pierwszy argument, który jest wystąpieniem `Example` klasy, i używa go do załadowania wartości pola wystąpienia prywatnego typu. `int` Drugi argument jest ładowany, a dwie liczby są mnożone. Jeśli wynik jest większy niż `int`, wartość zostanie obcięta i najbardziej znaczące bity są odrzucane. Metoda zwraca, z wartością zwracaną na stosie.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. Utwórz wystąpienie delegata (zadeklarowane w kroku 1) reprezentujące metodę dynamiczną, wywołując Przeciążenie <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> metody. Utworzenie delegata kończy metodę, a wszelkie dalsze próby zmiany metody — na przykład dodanie więcej MSIL — jest ignorowane.  
  
    > [!NOTE]
    > Metodę można wywołać wiele <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> razy, aby utworzyć delegatów powiązanych z innymi wystąpieniami typu docelowego.  
  
     Poniższy kod wiąże metodę z nowym wystąpieniem klasy, `Example` których pole testu prywatnego jest ustawione na 42. Oznacza to, że za każdym razem, gdy delegat jest wywoływany, wystąpienie `Example` jest przesyłane do pierwszego parametru metody.  
  
     Obiekt delegowany `OneParameter` jest używany, ponieważ pierwszy parametr metody zawsze otrzymuje wystąpienie `Example`. Gdy obiekt delegowany jest wywoływany, wymagany jest tylko drugi parametr.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje prostą metodę dynamiczną i metodę dynamiczną powiązaną z wystąpieniem klasy.  
  
 Prosta metoda dynamiczna przyjmuje jeden argument, 32-bitową liczbę całkowitą i zwraca kwadrat 64-bitowy tej liczby całkowitej. Delegat generyczny jest używany do wywołania metody.  
  
 Druga metoda dynamiczna ma dwa parametry typu `Example` i typu `int` (`Integer` w Visual Basic). Gdy metoda dynamiczna została utworzona, jest ona powiązana z wystąpieniem `Example`, przy użyciu ogólnego delegata z jednym argumentem typu. `int` Delegat nie ma argumentu typu `Example` , ponieważ pierwszy parametr metody zawsze otrzymuje powiązane wystąpienie. `Example` Gdy obiekt delegowany jest wywoływany, `int` zostanie dostarczony tylko argument. Ta metoda dynamiczna uzyskuje dostęp do prywatnego pola `Example` klasy i zwraca iloczyn pola prywatnego i `int` argumentu.  
  
 Przykładowy kod definiuje delegatów, których można użyć do wykonywania metod.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.Emit.DynamicMethod>
- [Używanie emisji odbicia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Scenariusze emisji metod dynamicznych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))
