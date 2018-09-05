---
title: 'Porady: symulowanie zdarzeń myszy i klawiatury w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
ms.openlocfilehash: 56c7d534d5428ff116c6de1aeffd9a31bd7a5063
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562676"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Porady: symulowanie zdarzeń myszy i klawiatury w kodzie
Windows Forms zapewnia kilka opcji symulowania programowo, myszy i klawiatury. Ten temat zawiera omówienie tych opcji.  
  
## <a name="simulating-mouse-input"></a>Symulowanie wejście myszy  
 Najlepszym sposobem Symulowanie zdarzeń myszy jest wywołać `On` *EventName* metody, która wywołuje zdarzenia myszy, które chcesz zasymulować. Ta opcja jest zwykle jest możliwe tylko w kontrolkach niestandardowych i formularzy, ponieważ metody, wywoływanie zdarzeń, które są chronione i nie są dostępne poza formularz lub formant. Na przykład poniższe kroki ilustrują zasymulować, klikając prawym przyciskiem myszy w kodzie.  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a>Aby programowo kliknij prawym przyciskiem myszy  
  
1.  Tworzenie <xref:System.Windows.Forms.MouseEventArgs> którego <xref:System.Windows.Forms.MouseEventArgs.Button%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> wartość.  
  
2.  Wywołaj <xref:System.Windows.Forms.Control.OnMouseClick%2A> metody, w tym <xref:System.Windows.Forms.MouseEventArgs> jako argument.  
  
 Aby uzyskać więcej informacji na temat kontrolek niestandardowych, zobacz [tworzenia kontrolek Windows Forms w czasie projektowania](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).  
  
 Istnieją inne sposoby, aby symulować wprowadzanie za pomocą myszy. Na przykład programowo ustawić właściwości formantu, który reprezentuje stan, który jest zwykle ustawiana tylko za pomocą myszy dane wejściowe (takie jak <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwość <xref:System.Windows.Forms.CheckBox> kontroli), lub możesz bezpośrednio wywołać delegata, który jest dołączony do zdarzenia należy Czy chcesz symulować.  
  
## <a name="simulating-keyboard-input"></a>Symulowanie danych wprowadzonych z klawiatury  
 Mimo że można symulować danych wprowadzonych z klawiatury, za pomocą strategii omówione powyżej na myszy dane wejściowe, Windows Forms zapewnia również <xref:System.Windows.Forms.SendKeys> klasy wysyłania naciśnięcia klawiszy do aktywnej aplikacji.  
  
> [!CAUTION]
>  Jeśli aplikacja jest przeznaczona do użytku międzynarodowe, z różnymi rodzajami klawiatury i korzystanie z <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> może przynieść nieprzewidywalne rezultaty i należy ich unikać.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SendKeys> Klasy zostało zaktualizowane dla środowiska .NET Framework 3.0 umożliwić jego użycia w aplikacjach, które są uruchamiane w systemie Windows Vista. Zwiększonych zabezpieczeń systemu Windows Vista (znane jako Kontrola konta użytkownika lub funkcji Kontrola konta użytkownika) zapobiega poprzedniej implementacji działać zgodnie z oczekiwaniami.  
>   
>  <xref:System.Windows.Forms.SendKeys> Klasy jest podatna na problemy dotyczące synchronizacji, które miały niektórzy deweloperzy w celu obejścia. Zaktualizowanej implementacji są nadal podatne na problemy dotyczące synchronizacji, ale jest teraz nieco szybszy i mogą wymagać zmian w rozwiązania. <xref:System.Windows.Forms.SendKeys> Klasy spróbuje najpierw użyć poprzedniej implementacji, a jeśli ono zawiedzie, korzysta z nowej implementacji. W rezultacie <xref:System.Windows.Forms.SendKeys> klasy może zachowywać się inaczej w różnych systemach operacyjnych. Ponadto, jeśli <xref:System.Windows.Forms.SendKeys> klasa korzysta z nowej implementacji <xref:System.Windows.Forms.SendKeys.SendWait%2A> metoda nie będzie czekać komunikaty mają być przetwarzane, gdy są one wysyłane do innego procesu.  
>   
>  Jeśli aplikacja zależy od spójne zachowanie niezależnie od systemu operacyjnego, możesz wymusić <xref:System.Windows.Forms.SendKeys> klasy, aby korzystać z nowej implementacji, dodając następujące ustawienie aplikacji do pliku app.config.  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  Aby wymusić <xref:System.Windows.Forms.SendKeys> klasy, aby użyć poprzedniego wdrożenia, należy użyć wartości `"JournalHook"` zamiast tego.  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a>Aby wysłać naciśnięcia klawiszy do tej samej aplikacji  
  
1.  Wywołaj <xref:System.Windows.Forms.SendKeys.Send%2A> lub <xref:System.Windows.Forms.SendKeys.SendWait%2A> metody <xref:System.Windows.Forms.SendKeys> klasy. Określony naciśnięć klawiszy zostanie odebrana przez aktywną kontrolkę w aplikacji. Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.SendKeys.Send%2A> zasymulować, naciskając klawisz ENTER, gdy użytkownik kliknie dwukrotnie powierzchnia formularza. W tym przykładzie założono <xref:System.Windows.Forms.Form> za pomocą jednego <xref:System.Windows.Forms.Button> kontrolkę, która ma indeks 0.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a>Aby wysłać naciśnięcia klawiszy do innej aplikacji  
  
1.  Aktywuj okna aplikacji, która będzie odbierać naciśnięcia klawiszy, a następnie wywołaj <xref:System.Windows.Forms.SendKeys.Send%2A> lub <xref:System.Windows.Forms.SendKeys.SendWait%2A> metody. Ponieważ nie istnieje metoda zarządzanych do aktywowania innej aplikacji, musi być wymusić skoncentrować się na inne aplikacje natywne metodami Windows. Następująca platforma używa przykładowy kod wywołana w celu wywołania `FindWindow` i `SetForegroundWindow` metody w celu aktywowania Kalkulator okna aplikacji, a następnie wywołania <xref:System.Windows.Forms.SendKeys.SendWait%2A> wydawania szereg obliczeń aplikacja Kalkulator.  
  
    > [!NOTE]
    >  Poprawne parametry `FindWindow` wywołań, który lokalizuje aplikacja Kalkulator różnią się zależnie od używanej wersji systemu Windows.  Poniższy kod umożliwia znalezienie aplikacja Kalkulator na [!INCLUDE[win7](../../../includes/win7-md.md)]. Na [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], zmień wartość pierwszego parametru "SciCalc". Spy ++ narzędzia, dołączonego do programu Visual Studio, można użyć do określenia poprawnych parametrów.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest kompletna aplikacja w poprzednich przykładach kodu.  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dane użytkownika w formularzach Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
