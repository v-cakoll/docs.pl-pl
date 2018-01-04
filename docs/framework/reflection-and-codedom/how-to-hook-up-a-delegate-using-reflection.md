---
title: "Porady: podłączanie delegata za pomocą odbicia"
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
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ff800eb78b07fc79193c2aa8cb71a461be2fc1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Porady: podłączanie delegata za pomocą odbicia
Gdy używasz odbicia do ładowania i uruchamiania zestawy, nie można używać funkcji języka, takich jak C# `+=` operator lub Visual Basic [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) do podpinanie zdarzeń. Poniższe procedury pokazują, jak Podłączanie istniejącą metodę do zdarzenia, uzyskując wszystkie wymagane typy przez odbicie i tworzenie dynamicznych metoda, za pomocą odbicia Emituj i podłącz go do zdarzenia.  
  
> [!NOTE]
>  Innym sposobem Podłączanie delegata obsługi zdarzeń, zobacz przykład kodu <xref:System.Reflection.EventInfo.AddEventHandler%2A> metody <xref:System.Reflection.EventInfo> klasy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Aby Podłączanie delegata za pomocą odbicia  
  
1.  Załaduj zestaw, który zawiera typ, który informuje o zdarzeniach. Zestawy są zazwyczaj ładowane z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Aby zachować w tym przykładzie jest proste, pochodnych formularza w bieżącym zestawie jest używana, więc <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda jest używana do załadowania bieżącego zestawu.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  Pobierz <xref:System.Type> obiekt reprezentujący typ i utworzyć wystąpienia typu. <xref:System.Activator.CreateInstance%28System.Type%29> Metoda jest używana w poniższym kodzie, ponieważ formularz ma konstruktora domyślnego. Istnieje kilka przeciążeń z <xref:System.Activator.CreateInstance%2A> metody można użyć, jeśli tworzysz typ nie ma domyślnego konstruktora. Nowe wystąpienie jest przechowywana jako typ <xref:System.Object> do obsługi fikcja że żaden element nie jest znany o zestawie. (Odbicia umożliwia pobieranie typów w zestawie bez wiedzy o nazwach z wyprzedzeniem.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  Pobierz <xref:System.Reflection.EventInfo> obiekt reprezentujący zdarzenia, a następnie użyj <xref:System.Reflection.EventInfo.EventHandlerType%2A> właściwości można pobrać typu delegata używane do obsługi zdarzenia. W poniższym kodzie <xref:System.Reflection.EventInfo> dla <xref:System.Windows.Forms.Control.Click> są uzyskiwane zdarzeń.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  Pobierz <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę, która obsługuje zdarzenie. Kod programu pełną w sekcji przykład w dalszej części tego tematu zawiera metodę, która pasuje do podpisu <xref:System.EventHandler> delegata, która obsługuje <xref:System.Windows.Forms.Control.Click> zdarzeń, ale można również generować metod dynamicznych w czasie wykonywania. Aby uzyskać więcej informacji zobacz procedurę towarzyszący generowania program obsługi zdarzeń w czasie wykonywania za pomocą metody dynamicznej.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  Utwórz wystąpienie obiektu delegowanego, przy użyciu <xref:System.Delegate.CreateDelegate%2A> metody. Ta metoda jest statyczna (`Shared` w języku Visual Basic), dlatego należy podać typ delegata. Przy użyciu przeciążeń <xref:System.Delegate.CreateDelegate%2A> które trwają <xref:System.Reflection.MethodInfo> jest zalecane.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  Pobierz `add` metodę dostępu i wywołać go do podłączenie zdarzenia. Wszystkie zdarzenia mają `add` metody dostępu i `remove` dostępu, które zostały ukryte za składnię języków wysokiego poziomu. Na przykład C# używa `+=` operatora podpinanie zdarzeń i używa języka Visual Basic [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md). Poniższy kod pobiera `add` akcesor <xref:System.Windows.Forms.Control.Click> zdarzeń i wywołuje ona późnym wiązaniem, przekazując to wystąpienie obiektu delegowanego. Argumenty muszą być przekazywane jako tablica.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  Przetestuj zdarzenia. Poniższy kod przedstawia formularz zdefiniowany w przykładzie kodu. Klikając formularz wywołuje program obsługi zdarzeń.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Aby wygenerować program obsługi zdarzeń w czasie wykonywania za pomocą metody dynamiczne  
  
1.  Metody obsługi zdarzeń mogą być generowane w czasie wykonywania za pomocą uproszczonego metod dynamicznych i emisja odbicia. Aby utworzyć program obsługi zdarzeń, należy typ zwracany i typy parametrów delegata. Te można uzyskać, sprawdzając delegata `Invoke` metody. Poniższy kod używa `GetDelegateReturnType` i `GetDelegateParameterTypes` metody, aby uzyskać te informacje. Kod dla tych metod można znaleźć w sekcji przykład w dalszej części tego tematu.  
  
     Nie jest konieczne nazwanie <xref:System.Reflection.Emit.DynamicMethod>, więc można pusty ciąg. W poniższym kodzie ostatni argument kojarzy z bieżącym typem, podając delegat dostęp do wszystkich publicznych i prywatnych elementów członkowskich z metody dynamicznej `Example` klasy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  Generowanie treści metody. Ta metoda ładuje ciągiem, wywołują przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody pobierającej ciąg, będzie wyświetlana wartość zwracana ze stosu (ponieważ program obsługi nie ma zwracanego typu) i zwraca. Aby dowiedzieć się więcej na temat emitowanie metod dynamicznych, zobacz [porady: definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  Zakończenie metody dynamicznej przez wywołanie jego <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody. Użyj `add` dostępu, aby dodać do listy wywołania zdarzenia delegata.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  Przetestuj zdarzenia. Poniższy kod załaduje formularz zdefiniowany w przykładzie kodu. Klikając formularz wywołuje zarówno programu obsługi zdarzeń wstępnie zdefiniowanych i obsługi zdarzeń emitowany.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak podłączenie istniejącą metodę ze zdarzeniem przy użyciu odbicia, a także sposób użycia <xref:System.Reflection.Emit.DynamicMethod> klasy Emituj metody w czasie wykonywania i podłącz go do zdarzenia.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawów dodatkowe są niezbędne do kompilacji z wiersza polecenia. W programie Visual Studio możesz dodać odwołania do System.Windows.Forms.dll, ponieważ w tym przykładzie jest aplikacji konsoli.  
  
-   Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe. Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 <xref:System.Activator.CreateInstance%2A>  
 <xref:System.Delegate.CreateDelegate%2A>  
 [Instrukcje: definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)
