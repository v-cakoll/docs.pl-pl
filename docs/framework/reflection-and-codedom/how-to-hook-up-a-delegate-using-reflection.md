---
title: 'Instrukcje: Podłączanie delegata za pomocą odbicia'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7c2956a222a47cea36abbc2f21da2d7e2061e09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314532"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Instrukcje: Podłączanie delegata za pomocą odbicia
Gdy używasz odbicia można załadować i uruchomić zestawów, nie można używać funkcji języka, takich jak C# `+=` operatora lub Visual Basic [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) do podłączania zdarzeń. Poniższe procedury pokazują, jak dołączyć istniejącą metodę do zdarzenia przez pobranie wszystkich typów wymaganych przez odbicie, a także jak utworzyć metodę dynamiczną za pomocą odbicia emisji i podłączyć ją do zdarzenia.  
  
> [!NOTE]
>  Innym sposobem Podłączanie delegata obsługi zdarzeń, zobacz przykład kodu dla <xref:System.Reflection.EventInfo.AddEventHandler%2A> metody <xref:System.Reflection.EventInfo> klasy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Aby Podłączanie delegata za pomocą odbicia  
  
1. Załaduj zestaw, który zawiera typ, który wywołuje zdarzenia. Zestawy są zazwyczaj załadowane <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. W celu uproszczenia w tym przykładzie zastosowano pochodnej formularza w bieżącym zestawie, więc <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda jest używana do ładowania bieżącego zestawu.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Pobierz <xref:System.Type> obiekt reprezentujący typ i utworzyć wystąpienie typu. <xref:System.Activator.CreateInstance%28System.Type%29> Metoda jest używana w poniższym kodzie, ponieważ formularza ma domyślnego konstruktora. Istnieje kilka innych przeciążeń <xref:System.Activator.CreateInstance%2A> metody można użyć, jeśli typ tworzenia nie ma domyślnego konstruktora. Nowe wystąpienie jest przechowywany jako typ <xref:System.Object> do utrzymania fikcja że żaden element nie jest znany o zestawie. (Odbicie umożliwia pobieranie typów w zestawie, nie wiedząc o tym ich nazwy z wyprzedzeniem.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Pobierz <xref:System.Reflection.EventInfo> obiekt reprezentujący zdarzenia, a następnie użyj <xref:System.Reflection.EventInfo.EventHandlerType%2A> właściwości, aby uzyskać typ delegata używany do obsługi zdarzeń. W poniższym kodzie <xref:System.Reflection.EventInfo> dla <xref:System.Windows.Forms.Control.Click> uzyskuje się zdarzenie.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Pobierz <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę, która obsługuje zdarzenie. Kod programu ukończone w części przykładu w dalszej części tego tematu zawiera metodę, która pasuje do podpisu <xref:System.EventHandler> delegować, która obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenia, ale można również wygenerować metod dynamicznych w czasie wykonywania. Aby uzyskać szczegółowe informacje zobacz procedurę towarzyszących do wygenerowania procedury obsługi zdarzeń w czasie wykonywania przy użyciu dynamicznej metody.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Utwórz wystąpienie delegata, za pomocą <xref:System.Delegate.CreateDelegate%2A> metody. Ta metoda jest statyczna (`Shared` w języku Visual Basic), dlatego wymagane jest podanie typu delegata. Za pomocą przeciążenia <xref:System.Delegate.CreateDelegate%2A> o <xref:System.Reflection.MethodInfo> jest zalecane.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Pobierz `add` metody dostępu i wywoływanie aby zaczepić zdarzenie. Wszystkie zdarzenia mają `add` metody dostępu i `remove` metody dostępu są ukrywane w składni języków wysokiego poziomu. Na przykład C# używa `+=` podpinanie zdarzeń i Visual Basic używa operatora [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md). Poniższy kod pobiera `add` akcesor <xref:System.Windows.Forms.Control.Click> zdarzeń, a następnie wywołuje on z późnym wiązaniem, przekazując to wystąpienie delegata. Argumenty muszą być przekazywane jako tablica.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Przetestuj zdarzenia. Poniższy kod przedstawia formularz zdefiniowany w przykładzie kodu. Klikając formularz wywołuje program obsługi zdarzeń.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Aby wygenerować procedurę obsługi zdarzeń w czasie wykonywania przy użyciu dynamicznej metody  
  
1. W czasie wykonywania za pomocą uproszczonego metody dynamiczne mogą być generowane metody obsługi zdarzeń i emisji odbicia. Do utworzenia programu obsługi zdarzeń, potrzebne jest typ zwracany i typy parametrów delegata. Te można uzyskać, sprawdzając pełnomocnika `Invoke` metody. Poniższy kod używa `GetDelegateReturnType` i `GetDelegateParameterTypes` metody, aby uzyskać te informacje. Kod dla tych metod można znaleźć w części przykładu w dalszej części tego tematu.  
  
     Nie jest konieczne nazwanie <xref:System.Reflection.Emit.DynamicMethod>, więc pusty ciąg może być używany. W poniższym kodzie, ostatni argument kojarzy metodę dynamiczną z bieżącym typem, zapewniając obiektu delegowanego dostępu do wszystkich publicznych i prywatnych składowych `Example` klasy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Generowanie treści metody. Ta metoda ładuje ciągu, wywołuje przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody, która przyjmuje ciąg, pojawi się wartość zwracaną ze stosu (ponieważ program obsługi nie ma zwracanego typu), a następnie zwraca. Aby dowiedzieć się więcej na temat emitowanie metod dynamicznych, zobacz [jak: Definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Wykonaj metodę dynamiczną, wywołując jego <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody. Użyj `add` dostępu, aby dodać delegata do listy wywołań dla zdarzenia.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Przetestuj zdarzenia. Poniższy kod ładuje formularz zdefiniowany w przykładzie kodu. Klikając formularz wywołuje program obsługi zdarzeń wstępnie zdefiniowanych i program obsługi zdarzeń emitowany.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dołączyć istniejącą metodę do zdarzenia przy użyciu odbicia, a także jak używać <xref:System.Reflection.Emit.DynamicMethod> klasy, aby emitować metodę w czasie wykonywania i podłączyć ją do zdarzenia.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod języka C# `using` instrukcji (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawu dodatkowe są wymagane do kompilowania z wiersza polecenia. W programie Visual Studio możesz dodać odwołanie do pliku System.Windows.Forms.dll, ponieważ w tym przykładzie jest to aplikacja konsoli.  
  
-   Skompilować kod w wierszu polecenia przy użyciu csc.exe i vbc.exe, cl.exe. Aby skompilować kod w programie Visual Studio, umieść go w szablonie projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Instrukcje: Definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)
