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
ms.openlocfilehash: 14a9694708b36b23ecef453d530ad3b939a046ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130115"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Porady: podłączanie delegata za pomocą odbicia
W przypadku używania odbicia do ładowania i uruchamiania zestawów nie można użyć funkcji języka, takich C# jak operator `+=` lub Visual Basic [AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md) , aby podłączyć zdarzenia. W poniższych procedurach pokazano, jak podłączyć istniejącą metodę do zdarzenia, pobierając wszystkie niezbędne typy poprzez odbicie i jak utworzyć metodę dynamiczną przy użyciu emisji odbicia i podłączyć ją do zdarzenia.  
  
> [!NOTE]
> Aby uzyskać inny sposób, aby podłączyć delegata obsługi zdarzeń, zobacz przykład kodu dla metody <xref:System.Reflection.EventInfo.AddEventHandler%2A> klasy <xref:System.Reflection.EventInfo>.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Aby podłączyć delegata przy użyciu odbicia  
  
1. Załaduj zestaw, który zawiera typ, który wywołuje zdarzenia. Zestawy są zwykle ładowane przy użyciu metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>. Aby zachować ten przykład prosty, używany jest formularz pochodny w bieżącym zestawie, dlatego Metoda <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> jest używana do ładowania bieżącego zestawu.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Pobierz obiekt <xref:System.Type> reprezentujący typ i Utwórz wystąpienie typu. Metoda <xref:System.Activator.CreateInstance%28System.Type%29> jest używana w poniższym kodzie, ponieważ formularz zawiera konstruktora bez parametrów. Istnieje kilka innych przeciążeń metody <xref:System.Activator.CreateInstance%2A>, których można użyć, jeśli tworzony typ nie ma konstruktora bez parametrów. Nowe wystąpienie jest przechowywane jako typ <xref:System.Object>, aby zachować fikcyjny, że nic nie jest znane o zestawie. (Odbicie umożliwia uzyskanie typów w zestawie bez poznania ich nazw z góry).  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Pobierz obiekt <xref:System.Reflection.EventInfo> reprezentujący zdarzenie i Użyj właściwości <xref:System.Reflection.EventInfo.EventHandlerType%2A>, aby uzyskać typ delegata używanego do obsługi zdarzenia. W poniższym kodzie zostanie uzyskany <xref:System.Reflection.EventInfo> dla zdarzenia <xref:System.Windows.Forms.Control.Click>.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Pobierz obiekt <xref:System.Reflection.MethodInfo> reprezentujący metodę, która obsługuje zdarzenie. Pełny kod programu w sekcji przykład w dalszej części tego tematu zawiera metodę, która pasuje do sygnatury delegata <xref:System.EventHandler>, który obsługuje zdarzenie <xref:System.Windows.Forms.Control.Click>, ale można również generować metody dynamiczne w czasie wykonywania. Aby uzyskać szczegółowe informacje, zobacz procedurę towarzyszącą w celu wygenerowania programu obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Utwórz wystąpienie delegata przy użyciu metody <xref:System.Delegate.CreateDelegate%2A>. Ta metoda jest statyczna (`Shared` w Visual Basic), więc należy podać typ delegata. Zalecane jest używanie przeciążeń <xref:System.Delegate.CreateDelegate%2A>, które pobierają <xref:System.Reflection.MethodInfo>.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Pobierz metodę dostępu `add` i Wywołaj ją, aby podłączyć zdarzenie. Wszystkie zdarzenia mają metodę dostępu `add` i metodę dostępu `remove`, która jest ukryta przez składnię języków wysokiego poziomu. Na przykład C# używa operatora `+=`, aby podłączyć zdarzenia, a Visual Basic używa [instrukcji AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md). Poniższy kod pobiera metodę dostępu `add` zdarzenia <xref:System.Windows.Forms.Control.Click> i wywołuje ją z późnym wiązaniem, przekazując w wystąpieniu delegata. Argumenty muszą być przekazane jako tablica.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Przetestuj zdarzenie. Poniższy kod przedstawia formularz zdefiniowany w przykładowym kodzie. Kliknięcie formularza wywołuje program obsługi zdarzeń.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Aby wygenerować procedurę obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej  
  
1. Metody obsługi zdarzeń mogą być generowane w czasie wykonywania przy użyciu uproszczonych metod dynamicznych i emisji odbicia. Do skonstruowania procedury obsługi zdarzeń wymagany jest typ zwracany i typy parametrów delegata. Można je uzyskać, badając metodę `Invoke` delegata. Poniższy kod używa metod `GetDelegateReturnType` i `GetDelegateParameterTypes`, aby uzyskać te informacje. Kod dla tych metod można znaleźć w sekcji przykład w dalszej części tego tematu.  
  
     Nie trzeba określać nazwy <xref:System.Reflection.Emit.DynamicMethod>, więc można użyć pustego ciągu. W poniższym kodzie, ostatni argument kojarzy metodę dynamiczną z bieżącym typem, dając delegata dostęp do wszystkich publicznych i prywatnych członków klasy `Example`.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Generuj treść metody. Ta metoda ładuje ciąg, wywołuje Przeciążenie metody <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>, która pobiera ciąg, wyświetla wartość zwracaną przez stos (ponieważ program obsługi nie ma zwracanego typu) i zwraca. Aby dowiedzieć się więcej o emitowaniu metod dynamicznych, zobacz [How to: define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Ukończ metodę dynamiczną, wywołując metodę <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>. Użyj metody dostępu `add`, aby dodać delegata do listy wywołań dla zdarzenia.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Przetestuj zdarzenie. Poniższy kod ładuje formularz zdefiniowany w przykładowym kodzie. Kliknięcie formularza wywołuje zarówno wstępnie zdefiniowaną procedurę obsługi zdarzeń, jak i wyemitowaną procedurę obsługi zdarzeń.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak podłączyć istniejącą metodę do zdarzenia przy użyciu odbicia, a także jak użyć klasy <xref:System.Reflection.Emit.DynamicMethod> do emisji metody w czasie wykonywania i podłączania jej do zdarzenia.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Instrukcje: definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md)
- [Odbicie](reflection.md)
