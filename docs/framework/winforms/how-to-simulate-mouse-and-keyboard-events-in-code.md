---
title: 'Porady: symulowanie zdarzeń myszy i klawiatury w kodzie'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 387b73d4e1820d71d163fddebe8fe9f24e4ff56e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Porady: symulowanie zdarzeń myszy i klawiatury w kodzie
Formularze systemu Windows zapewnia kilka opcji programowo symulując myszy i klawiatury. Ten temat zawiera omówienie tych opcji.  
  
## <a name="simulating-mouse-input"></a>Symuluje wejście myszy  
 Najlepszym sposobem Symulowanie zdarzeń myszy jest wywołać `On` *EventName* metodę, która wywołuje zdarzenie myszy chcesz symulować. Ta opcja jest zwykle możliwe tylko w kontrolkach niestandardowych i formularze, ponieważ metody, które uruchamiają zdarzenia są chronione i nie można uzyskać dostępu do poza formularz lub formant. Na przykład poniższe kroki przedstawiają symulowanie, klikając prawym przyciskiem myszy w kodzie.  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a>Aby programowo kliknij prawym przyciskiem myszy  
  
1.  Utwórz <xref:System.Windows.Forms.MouseEventArgs> których <xref:System.Windows.Forms.MouseEventArgs.Button%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> wartość.  
  
2.  Wywołanie <xref:System.Windows.Forms.Control.OnMouseClick%2A> metody z tym <xref:System.Windows.Forms.MouseEventArgs> jako argument.  
  
 Aby uzyskać więcej informacji na formantów niestandardowych, zobacz [opracowywanie formantów formularzy systemu Windows w czasie projektowania](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).  
  
 Istnieją inne sposoby symulować myszą. Na przykład programowane Ustawianie właściwości formantu, która reprezentuje stan, który jest zwykle ustawiana za pośrednictwem wejście myszy (takich jak <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwość <xref:System.Windows.Forms.CheckBox> kontroli), lub możesz bezpośrednio wywołać delegata, który jest dołączony do zdarzenia należy Czy chcesz symulować.  
  
## <a name="simulating-keyboard-input"></a>Symuluje wejście klawiatury  
 Mimo że można symulować klawiatury przy użyciu strategii opisanych powyżej dla wejście myszy formularzy systemu Windows udostępnia również <xref:System.Windows.Forms.SendKeys> klasy wysyłania naciśnięcia klawiszy do aktywnej aplikacji.  
  
> [!CAUTION]
>  Jeśli aplikacja jest przeznaczona do użycia międzynarodowych z różnymi klawiatury, użycie <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> może spowodować nieprzewidywalne skutki i należy unikać.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SendKeys> Klasa została zaktualizowana dla środowiska .NET Framework 3.0 umożliwić jej użycie w aplikacji działających w systemie Windows Vista. Zwiększone zabezpieczenia systemu Windows Vista (nazywanych Kontrola konta użytkownika lub UAC) zapobiega poprzedniej implementacji działać zgodnie z oczekiwaniami.  
>   
>  <xref:System.Windows.Forms.SendKeys> Klasy są podatne na problemy dotyczące synchronizacji, które miały niektórzy deweloperzy obejścia. Zaktualizowane wdrożenia są nadal podatne na problemy dotyczące synchronizacji, ale jest nieco większą i mogą wymagać zmian do rozwiązania. <xref:System.Windows.Forms.SendKeys> Klasa próbuje użyć poprzedniej implementacji najpierw, a w przypadku niepowodzenia korzysta z nowej implementacji. W związku z tym <xref:System.Windows.Forms.SendKeys> klasy może zachowywać się inaczej w różnych systemach operacyjnych. Ponadto, jeśli <xref:System.Windows.Forms.SendKeys> klasa korzysta z nowej implementacji <xref:System.Windows.Forms.SendKeys.SendWait%2A> — metoda nie będzie oczekiwał na komunikaty do przetwarzania, gdy są one wysyłane do innego procesu.  
>   
>  Jeśli aplikacja opiera się na spójne zachowanie niezależnie od systemu operacyjnego, można wymusić <xref:System.Windows.Forms.SendKeys> klasę, aby korzystać z nowej implementacji, dodając następujące ustawienie aplikacji w pliku app.config.  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  Aby wymusić <xref:System.Windows.Forms.SendKeys> klasy do poprzedniej implementacji, należy użyć wartości `"JournalHook"` zamiast tego.  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a>Aby wysłać naciśnięcia klawiszy do tej samej aplikacji  
  
1.  Wywołanie <xref:System.Windows.Forms.SendKeys.Send%2A> lub <xref:System.Windows.Forms.SendKeys.SendWait%2A> metody <xref:System.Windows.Forms.SendKeys> klasy. Określony naciśnięcia klawiszy będą odbierane przez formant aktywnej aplikacji. Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.SendKeys.Send%2A> do symulowania naciśnięcie klawisza ENTER, gdy użytkownik kliknie dwukrotnie powierzchni formularza. W tym przykładzie założono <xref:System.Windows.Forms.Form> za pomocą jednej <xref:System.Windows.Forms.Button> formantu, który ma indeks 0.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a>Aby wysłać naciśnięcia klawiszy do innej aplikacji  
  
1.  Aktywacja okna aplikacji, który będzie wyświetlany naciśnięcia klawiszy, a następnie wywołać <xref:System.Windows.Forms.SendKeys.Send%2A> lub <xref:System.Windows.Forms.SendKeys.SendWait%2A> metody. Ponieważ nie istnieje metoda zarządzanych do aktywowania innej aplikacji, należy użyć natywnego Windows metody na wymuszanie fokus na inne aplikacje. Następująca platforma używa przykładowy kod wywołania do wywołania `FindWindow` i `SetForegroundWindow` aktywować Kalkulator okna aplikacji, a następnie wywołania metody <xref:System.Windows.Forms.SendKeys.SendWait%2A> wystawianie szereg obliczeń do Kalkulatora aplikacji.  
  
    > [!NOTE]
    >  Poprawne parametry `FindWindow` wywołanie, która lokalizuje aplikacji Kalkulator różnić w zależności od używanej wersji systemu Windows.  Poniższy kod umożliwia znalezienie aplikacji Kalkulator na [!INCLUDE[win7](../../../includes/win7-md.md)]. Na [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], Zmień pierwszy parametr "SciCalc". Spy ++ narzędzia, dołączonego do programu Visual Studio, można użyć do określenia poprawnych parametrów.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod jest kompletna aplikacja dla w poprzednich przykładach kodu.  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dane użytkownika w formularzach Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
