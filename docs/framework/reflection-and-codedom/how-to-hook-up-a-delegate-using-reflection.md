---
title: 'Instrukcje: Podłączanie delegata za pomocą odbicia'
description: Zobacz jak podłączyć delegata przy użyciu odbicia w programie .NET. Połącz istniejącą metodę ze zdarzeniem, pobierając niezbędne typy poprzez odbicie.
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
ms.openlocfilehash: b5d93efd278a53a4e6382f2321918e58ead55899
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865089"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Instrukcje: Podłączanie delegata za pomocą odbicia
W przypadku używania odbicia do ładowania i uruchamiania zestawów nie można użyć funkcji języka, takich jak `+=` operator języka C# lub Visual Basic [AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md) , aby podłączyć zdarzenia. W poniższych procedurach pokazano, jak podłączyć istniejącą metodę do zdarzenia, pobierając wszystkie niezbędne typy poprzez odbicie i jak utworzyć metodę dynamiczną przy użyciu emisji odbicia i podłączyć ją do zdarzenia.  
  
> [!NOTE]
> Aby móc podłączyć delegata obsługi zdarzeń, zobacz przykład kodu dla <xref:System.Reflection.EventInfo.AddEventHandler%2A> metody <xref:System.Reflection.EventInfo> klasy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Aby podłączyć delegata przy użyciu odbicia  
  
1. Załaduj zestaw, który zawiera typ, który wywołuje zdarzenia. Zestawy są zwykle ładowane przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Aby zachować ten przykład prosty, używany jest formularz pochodny w bieżącym zestawie, dlatego <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> Metoda jest używana do ładowania bieżącego zestawu.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Pobierz <xref:System.Type> obiekt reprezentujący typ i Utwórz wystąpienie typu. <xref:System.Activator.CreateInstance%28System.Type%29>Metoda jest używana w poniższym kodzie, ponieważ formularz zawiera konstruktora bez parametrów. Istnieje kilka innych przeciążeń <xref:System.Activator.CreateInstance%2A> metody, których można użyć, jeśli tworzony typ nie ma konstruktora bez parametrów. Nowe wystąpienie jest przechowywane jako typ <xref:System.Object> do obsługi fikcyjnego, który nie jest znany o zestawie. (Odbicie umożliwia uzyskanie typów w zestawie bez poznania ich nazw z góry).  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Pobierz <xref:System.Reflection.EventInfo> obiekt reprezentujący zdarzenie i Użyj <xref:System.Reflection.EventInfo.EventHandlerType%2A> właściwości, aby uzyskać typ delegata użytego do obsłużenia zdarzenia. W poniższym kodzie <xref:System.Reflection.EventInfo> <xref:System.Windows.Forms.Control.Click> jest uzyskiwany dla zdarzenia.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Pobierz <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę, która obsługuje zdarzenie. Pełny kod programu w sekcji przykład w dalszej części tego tematu zawiera metodę, która pasuje do podpisu <xref:System.EventHandler> delegata, który obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie, ale można również generować metody dynamiczne w czasie wykonywania. Aby uzyskać szczegółowe informacje, zobacz procedurę towarzyszącą w celu wygenerowania programu obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Utwórz wystąpienie delegata przy użyciu <xref:System.Delegate.CreateDelegate%2A> metody. Ta metoda jest statyczna ( `Shared` w Visual Basic), więc należy podać typ delegata. Zalecane jest użycie przeciążenia <xref:System.Delegate.CreateDelegate%2A> , które to zajmie <xref:System.Reflection.MethodInfo> .  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Pobierz `add` metodę dostępu i Wywołaj ją, aby podłączyć zdarzenie. Wszystkie zdarzenia mają `add` akcesor i `remove` metodę dostępu, która jest ukryta przez składnię języków wysokiego poziomu. Na przykład, C# używa `+=` operatora, aby podłączyć zdarzenia, a Visual Basic używa [instrukcji AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md). Poniższy kod pobiera `add` metodę dostępu dla <xref:System.Windows.Forms.Control.Click> zdarzenia i wywołuje ją z późnym wiązaniem, przekazując w wystąpieniu delegata. Argumenty muszą być przekazane jako tablica.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Przetestuj zdarzenie. Poniższy kod przedstawia formularz zdefiniowany w przykładowym kodzie. Kliknięcie formularza wywołuje program obsługi zdarzeń.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Aby wygenerować procedurę obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej  
  
1. Metody obsługi zdarzeń mogą być generowane w czasie wykonywania przy użyciu uproszczonych metod dynamicznych i emisji odbicia. Do skonstruowania procedury obsługi zdarzeń wymagany jest typ zwracany i typy parametrów delegata. Można je uzyskać, badając metodę delegata `Invoke` . Poniższy kod używa `GetDelegateReturnType` metod i, `GetDelegateParameterTypes` Aby uzyskać te informacje. Kod dla tych metod można znaleźć w sekcji przykład w dalszej części tego tematu.  
  
     Nazwa nie jest konieczna <xref:System.Reflection.Emit.DynamicMethod> , więc można użyć pustego ciągu. W poniższym kodzie, ostatni argument kojarzy metodę dynamiczną z bieżącym typem, dając delegata dostęp do wszystkich publicznych i prywatnych członków `Example` klasy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Generuj treść metody. Ta metoda ładuje ciąg, wywołuje Przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody, która pobiera ciąg znaków, wyświetla wartość zwracaną przez stos (ponieważ program obsługi nie ma zwracanego typu) i zwraca. Aby dowiedzieć się więcej o emitowaniu metod dynamicznych, zobacz [How to: define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Ukończ metodę dynamiczną, wywołując <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metodę. Użyj `add` metody dostępu, aby dodać delegata do listy wywołań dla zdarzenia.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Przetestuj zdarzenie. Poniższy kod ładuje formularz zdefiniowany w przykładowym kodzie. Kliknięcie formularza wywołuje zarówno wstępnie zdefiniowaną procedurę obsługi zdarzeń, jak i wyemitowaną procedurę obsługi zdarzeń.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak podłączyć istniejącą metodę do zdarzenia przy użyciu odbicia, a także jak użyć <xref:System.Reflection.Emit.DynamicMethod> klasy do emisji metody w czasie wykonywania i podłączania do zdarzenia.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Instrukcje: Definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md)
- [Odbicie](reflection.md)
