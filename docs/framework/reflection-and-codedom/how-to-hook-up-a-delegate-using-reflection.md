---
title: 'Porady: podłączanie delegata za pomocą odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: d748d9f8bdd0b4d831880548d4aceb1c77a0b0c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180503"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Porady: podłączanie delegata za pomocą odbicia
Podczas korzystania z odbicia do ładowania i uruchamiania zestawów, `+=` nie można użyć funkcji języka, takich jak operator Języka C# lub Visual Basic [AddHandler instrukcji](../../visual-basic/language-reference/statements/addhandler-statement.md) do podłączania zdarzeń. Poniższe procedury pokazują, jak podłączyć istniejącą metodę do zdarzenia, uzyskując wszystkie niezbędne typy poprzez odbicie i jak utworzyć metodę dynamiczną przy użyciu odbicia emitować i podłączyć go do zdarzenia.  
  
> [!NOTE]
> Aby uzyskać inny sposób, aby podłączyć delegata obsługi <xref:System.Reflection.EventInfo.AddEventHandler%2A> zdarzeń, <xref:System.Reflection.EventInfo> zobacz przykład kodu dla metody klasy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Aby podłączyć delegata przy użyciu odbicia  
  
1. Załaduj zestaw, który zawiera typ, który wywołuje zdarzenia. Zestawy są zwykle ładowane z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Aby ten przykład był prosty, używany jest formularz pochodny <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> w bieżącym złożeniu, więc metoda jest używana do ładowania bieżącego złożenia.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Pobierz <xref:System.Type> obiekt reprezentujący typ i utwórz wystąpienie typu. Metoda <xref:System.Activator.CreateInstance%28System.Type%29> jest używana w poniższym kodzie, ponieważ formularz ma konstruktora bez parametrów. Istnieje kilka innych przeciążeń <xref:System.Activator.CreateInstance%2A> metody, które można użyć, jeśli typ, który tworzysz nie ma konstruktora bez parametrów. Nowe wystąpienie jest <xref:System.Object> przechowywane jako typ, aby zachować fikcję, że nic nie wiadomo o zestawie. (Odbicie pozwala uzyskać typy w zestawie, nie znając ich nazw z wyprzedzeniem.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Pobierz <xref:System.Reflection.EventInfo> obiekt reprezentujący zdarzenie i <xref:System.Reflection.EventInfo.EventHandlerType%2A> użyj właściwości, aby uzyskać typ delegata używanego do obsługi zdarzenia. W poniższym <xref:System.Reflection.EventInfo> kodzie <xref:System.Windows.Forms.Control.Click> uzyskuje się zdarzenie.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Pobierz <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę, która obsługuje zdarzenie. Pełny kod programu w sekcji Przykład w dalszej części tego <xref:System.EventHandler> tematu zawiera metodę, która pasuje do podpisu pełnomocnika, który obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie, ale można również wygenerować metody dynamiczne w czasie wykonywania. Aby uzyskać szczegółowe informacje, zobacz procedurę towarzyszącą, aby wygenerować program obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Utwórz wystąpienie delegata <xref:System.Delegate.CreateDelegate%2A> przy użyciu metody. Ta metoda jest`Shared` statyczna (w języku Visual Basic), więc należy podać typ delegata. Zaleca się użycie <xref:System.Delegate.CreateDelegate%2A> przeciążenia <xref:System.Reflection.MethodInfo> tego podjęcia.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Pobierz `add` metody akcesora i wywołać go, aby podłączyć zdarzenie. Wszystkie zdarzenia `add` mają akcesor i `remove` akcesor, które są ukryte przez składnię języków wysokiego poziomu. Na przykład C# używa `+=` operatora do podłączania zdarzeń, a visual basic używa [AddHandler instrukcji](../../visual-basic/language-reference/statements/addhandler-statement.md). Poniższy kod `add` pobiera akcesor <xref:System.Windows.Forms.Control.Click> zdarzenia i wywołuje go późno związane, przekazywanie w wystąpieniu delegata. Argumenty muszą być przekazywane jako tablica.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Przetestuj zdarzenie. Poniższy kod przedstawia formularz zdefiniowany w przykładzie kodu. Kliknięcie formularza wywołuje program obsługi zdarzeń.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Aby wygenerować program obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej  
  
1. Metody obsługi zdarzeń mogą być generowane w czasie wykonywania, przy użyciu lekkich metod dynamicznych i emitują odbicie. Aby utworzyć program obsługi zdarzeń, potrzebujesz typu zwracanego i typów parametrów pełnomocnika. Można je uzyskać, badając metodę `Invoke` delegata. Poniższy kod używa `GetDelegateReturnType` `GetDelegateParameterTypes` i metody, aby uzyskać te informacje. Kod dla tych metod można znaleźć w przykładowej sekcji w dalszej części tego tematu.  
  
     Nie jest konieczne, <xref:System.Reflection.Emit.DynamicMethod>aby nazwać , więc można użyć pustego ciągu. W poniższym kodzie ostatni argument kojarzy metodę dynamiczną z bieżącym typem, dając pełnomocnikowi dostęp do wszystkich publicznych i prywatnych członków `Example` klasy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Generowanie treści metody. Ta metoda ładuje ciąg, wywołuje przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody, która przyjmuje ciąg, wyskakuje wartość zwracaną ze stosu (ponieważ program obsługi nie ma typu zwracanego) i zwraca. Aby dowiedzieć się więcej na temat emitowania metod dynamicznych, zobacz [Jak: Definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Ukończ metodę <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> dynamiczną, wywołując jej metodę. Użyj `add` akcesora, aby dodać pełnomocnika do listy wywołań zdarzenia.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Przetestuj zdarzenie. Poniższy kod ładuje formularz zdefiniowany w przykładzie kodu. Kliknięcie formularza wywołuje zarówno wstępnie zdefiniowany program obsługi zdarzeń, jak i program obsługi zdarzeń emitowanych.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak podłączyć istniejącą metodę do zdarzenia <xref:System.Reflection.Emit.DynamicMethod> przy użyciu odbicia, a także jak używać klasy do emitowania metody w czasie wykonywania i podłączyć ją do zdarzenia.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Porady: definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md)
- [Odbicie](reflection.md)
