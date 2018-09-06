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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 865d9aa6806e00bb9cf7b3991b4f323d361cbb63
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785303"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Porady: definiowanie i wykonywanie metod dynamicznych
Poniższe procedury pokazują, jak zdefiniować i wykonać prostą metodę dynamiczną i metodę dynamiczną, która jest powiązana z wystąpienia klasy. Aby uzyskać więcej informacji na temat metod dynamicznych, zobacz <xref:System.Reflection.Emit.DynamicMethod> klasy i [odbicia emitowanie dynamicznych scenariusze metod](https://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Aby zdefiniować i wykonać metodę dynamiczną  
  
1.  Deklaracja typu delegowanego wykonać metodę. Należy rozważyć użycie Delegat ogólny, aby zminimalizować liczbę typy delegatów, czego potrzebujesz do deklarowania. Poniższy kod deklaruje delegować dwa typy, które mogłyby zostać użyte do `SquareIt` metoda i jeden z nich jest ogólny.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  Utwórz tablicę, która określa typy parametrów dla metody dynamicznej. W tym przykładzie jest jedynym parametrem `int` (`Integer` w języku Visual Basic), więc tablica ma tylko jeden element.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  Utwórz <xref:System.Reflection.Emit.DynamicMethod>. W tym przykładzie nosi nazwę metody `SquareIt`.  
  
    > [!NOTE]
    >  Nie jest konieczne nadać nazwy metody dynamiczne, a nie można wywołać według nazwy. Wiele metod dynamicznych może mieć takiej samej nazwie. Jednak nazwa jest wyświetlana w stosy wywołań i mogą być przydatne podczas debugowania.  
  
     Typ wartości zwracanej jest określony jako `long`. Metoda jest skojarzony z modułem, który zawiera `Example` klasy, która zawiera przykładowy kod. Wszelkie załadowanym module może być określony. Działa metodę dynamiczną, takich jak poziomie modułu `static` — metoda (`Shared` w języku Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  Emituj treści metody. W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do emitowania języka Microsoft intermediate language (MSIL). Alternatywnie <xref:System.Reflection.Emit.DynamicILInfo> obiekt może służyć w połączeniu z generatorów kodu niezarządzanego do wysyłania treści metody dla <xref:System.Reflection.Emit.DynamicMethod>.  
  
     MSIL, w tym przykładzie ładuje argumentu, czyli `int`, na stosie, konwertuje ją na wartość `long`, duplikaty `long`i mnoży dwie liczby. Spowoduje to, że wynik kwadratów na stosie, a metoda ma na celu będzie zwracany.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  Utwórz wystąpienie delegata (deklaracja w kroku 1), który reprezentuje metodę dynamiczną, wywołując <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody. Utworzenie obiektu delegowanego zakończeniu metody i dowolne dalsze próby zmienić metodę — na przykład dodanie MSIL więcej — są ignorowane. Poniższy kod tworzy delegata i wywołuje się, używając delegata ogólnego.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Aby zdefiniować i wykonać metodę dynamiczną, która jest powiązana z obiektem  
  
1.  Deklaracja typu delegowanego wykonać metodę. Należy rozważyć użycie Delegat ogólny, aby zminimalizować liczbę typy delegatów, czego potrzebujesz do deklarowania. Poniższy kod deklaruje typ delegata ogólnego, który może służyć do wykonywania dowolną metodą mającą jeden parametr i wartość zwracaną lub metody za pomocą dwóch parametrów i wartość zwracana, jeśli delegat jest powiązana z obiektem.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  Utwórz tablicę, która określa typy parametrów dla metody dynamicznej. Jeśli delegata metody reprezentująca ma być powiązana z obiektem, pierwszy parametr musi być zgodna z typu delegata jest powiązany z. W tym przykładzie są dwa parametry typu `Example` i typ `int` (`Integer` w języku Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  Utwórz <xref:System.Reflection.Emit.DynamicMethod>. W tym przykładzie metoda nie ma nazwy. Typ wartości zwracanej jest określony jako `int` (`Integer` w języku Visual Basic). Metoda ma dostęp do prywatnych i chronionych elementów członkowskich `Example` klasy.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  Emituj treści metody. W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do emitowania języka Microsoft intermediate language (MSIL). Alternatywnie <xref:System.Reflection.Emit.DynamicILInfo> obiekt może służyć w połączeniu z generatorów kodu niezarządzanego do wysyłania treści metody dla <xref:System.Reflection.Emit.DynamicMethod>.  
  
     MSIL, w tym przykładzie ładuje pierwszy argument, który jest wystąpieniem elementu `Example` klasy i używa go do załadowania wartości pola prywatnego wystąpienia typu `int`. Drugi argument jest ładowany i są mnożone dwóch liczb. Jeśli wynik jest większy niż `int`, wartość zostanie obcięta i najbardziej znaczące bity są odrzucane. Metoda zwraca z wartością zwracaną na stosie.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  Utwórz wystąpienie delegata (deklaracja w kroku 1), który reprezentuje metodę dynamiczną, wywołując <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> przeciążenie metody. Utworzenie obiektu delegowanego zakończeniu metody i dowolne dalsze próby zmienić metodę — na przykład dodanie MSIL więcej — są ignorowane.  
  
    > [!NOTE]
    >  Możesz wywołać <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda kilka razy do tworzenia obiektów delegowanych, powiązany z innych wystąpień typu docelowego.  
  
     Poniższy kod tworzy powiązanie metody nowe wystąpienie klasy `Example` klasy, których pole prywatne testu jest ustawiona wartość 42. Oznacza to, każdorazowo, obiekt delegowany jest wywoływany wystąpienie `Example` jest przekazywany do pierwszego parametru metody.  
  
     Delegat `OneParameter` jest używany, ponieważ pierwszy parametr metody zawsze będzie otrzymywał wystąpienie `Example`. Gdy obiekt delegowany jest wywoływany, drugi parametr jest wymagany.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, prostą metodę dynamiczną i metodę dynamiczną, która jest powiązana z wystąpienia klasy.  
  
 Prostą metodę dynamiczną przyjmuje jeden argument, 32-bitową liczbę całkowitą i zwraca 64-bitowych kwadrat tej liczby całkowitej. Delegat ogólny jest używana do wywołania metody.  
  
 Druga metoda dynamiczna ma dwa parametry typu `Example` i typ `int` (`Integer` w języku Visual Basic). Po utworzeniu metodę dynamiczną, jest powiązany do wystąpienia `Example`, za pomocą Delegat ogólny, który ma jeden argument typu `int`. Delegat nie ma argument typu `Example` ponieważ pierwszy parametr metody zawsze będzie otrzymywał powiązanej wystąpienia `Example`. Gdy obiekt delegowany jest wywoływany, tylko `int` argumentu. Ta metoda dynamiczna uzyskuje dostęp do pola prywatnego `Example` klasy i zwraca iloczyn pole prywatne i `int` argumentu.  
  
 Przykładowy kod definiuje delegatów, które mogą służyć do wykonywania metody.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod języka C# `using` instrukcji (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawu dodatkowe są wymagane.  
  
-   Skompilować kod w wierszu polecenia przy użyciu csc.exe i vbc.exe, cl.exe. Aby skompilować kod w programie Visual Studio, umieść go w szablonie projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [Używanie emisji odbicia](https://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Scenariusze metod dynamicznych emisji odbicia](https://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
