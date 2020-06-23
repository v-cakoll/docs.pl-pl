---
title: 'Instrukcje: Symulowanie zdarzeń myszy i klawiatury w kodzie'
description: Dowiedz się, jak używać opcji Windows Forms zapewnia symulowanie danych wejściowych myszy i klawiatury.
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
ms.openlocfilehash: 9b453787f7fa7f5041f75e04d65557a0a3838bee
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904367"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Instrukcje: Symulowanie zdarzeń myszy i klawiatury w kodzie

Windows Forms oferuje kilka opcji programistycznego symulowania danych wejściowych myszy i klawiatury. Ten temat zawiera omówienie tych opcji.

## <a name="simulating-mouse-input"></a>Symulowanie danych wejściowych myszy

Najlepszym sposobem symulowania zdarzeń myszy jest wywołanie `On` metody *EventName* , która wywołuje zdarzenie myszy, które ma zostać symulowane. Ta opcja jest zazwyczaj możliwa tylko w kontrolkach niestandardowych i formularzach, ponieważ metody, które powodują wygenerowanie zdarzeń, są chronione i nie można uzyskać do nich dostępu poza formantem lub formularzem. Na przykład poniższe kroki ilustrują sposób symulowania kliknięcia prawego przycisku myszy w kodzie.

#### <a name="to-programmatically-click-the-right-mouse-button"></a>Aby programowo kliknąć prawym przyciskiem myszy

1. Utwórz <xref:System.Windows.Forms.MouseEventArgs> Właściwość, której <xref:System.Windows.Forms.MouseEventArgs.Button%2A> właściwości jest ustawiona na <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> wartość.

2. Wywołaj <xref:System.Windows.Forms.Control.OnMouseClick%2A> metodę, używając <xref:System.Windows.Forms.MouseEventArgs> jako argumentu.

Aby uzyskać więcej informacji na temat kontrolek niestandardowych, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](./controls/developing-windows-forms-controls-at-design-time.md).

Istnieją inne sposoby symulowania danych wejściowych myszy. Na przykład można programowo ustawić właściwość kontrolki, która reprezentuje stan, który jest zazwyczaj ustawiany za pomocą danych wejściowych myszy (takich jak <xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość <xref:System.Windows.Forms.CheckBox> kontrolki), lub bezpośrednio wywołać delegata, który jest dołączony do zdarzenia, które ma zostać symulowane.

## <a name="simulating-keyboard-input"></a>Symulowanie danych wejściowych z klawiatury

Chociaż można symulować dane wejściowe z klawiatury przy użyciu strategii omówionych powyżej dla danych wejściowych myszy, Windows Forms udostępnia również <xref:System.Windows.Forms.SendKeys> klasę do wysyłania naciśnięć klawiszy do aktywnej aplikacji.

> [!CAUTION]
> Jeśli aplikacja jest przeznaczona do użytku międzynarodowego z różnymi klawiaturami, użycie <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> może dać nieprzewidywalne wyniki i należy je unikać.

> [!NOTE]
> <xref:System.Windows.Forms.SendKeys>Klasa została zaktualizowana dla .NET Framework 3,0, aby umożliwić jej używanie w aplikacjach uruchamianych w systemie Windows Vista. Ulepszone zabezpieczenia systemu Windows Vista (nazywanego kontrolą konta użytkownika lub UAC) uniemożliwiają działanie poprzedniej implementacji zgodnie z oczekiwaniami.
>
> <xref:System.Windows.Forms.SendKeys>Klasa jest podatna na problemy z chronometrażem, w przypadku których niektórzy deweloperzy musieli obejść. Zaktualizowana implementacja jest nadal podatna na problemy z chronometrażem, ale jest nieco szybsza i może wymagać wprowadzenia zmian w obejść. <xref:System.Windows.Forms.SendKeys>Klasa spróbuje najpierw użyć poprzedniej implementacji, a jeśli to się nie powiedzie, użyje nowej implementacji. W związku z tym <xref:System.Windows.Forms.SendKeys> Klasa może zachowywać się inaczej w różnych systemach operacyjnych. Ponadto, gdy <xref:System.Windows.Forms.SendKeys> Klasa używa nowej implementacji, <xref:System.Windows.Forms.SendKeys.SendWait%2A> Metoda nie będzie czekać na przetwarzanie komunikatów, gdy są wysyłane do innego procesu.
>
> Jeśli aplikacja korzysta ze spójności spójnej niezależnie od systemu operacyjnego, można wymusić, <xref:System.Windows.Forms.SendKeys> Aby Klasa korzystała z nowej implementacji, dodając do pliku app.config następujące ustawienie aplikacji.
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> Aby wymusić <xref:System.Windows.Forms.SendKeys> użycie poprzedniej implementacji przez klasę, użyj `"JournalHook"` zamiast niej wartości.

#### <a name="to-send-a-keystroke-to-the-same-application"></a>Aby wysłać naciśnięcie klawisza do tej samej aplikacji

1. Wywoływanie <xref:System.Windows.Forms.SendKeys.Send%2A> <xref:System.Windows.Forms.SendKeys.SendWait%2A> metody lub <xref:System.Windows.Forms.SendKeys> klasy. Określone nacionięcia klawiszy zostaną odebrane przez aktywną kontrolę aplikacji. Poniższy przykład kodu używa <xref:System.Windows.Forms.SendKeys.Send%2A> do symulowania naciskania klawisza ENTER, gdy użytkownik kliknie dwukrotnie powierzchnię formularza. W tym przykładzie przyjęto założenie, <xref:System.Windows.Forms.Form> że z pojedynczym <xref:System.Windows.Forms.Button> formantem ma indeks karty równy 0.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a>Aby wysłać naciśnięcie klawisza do innej aplikacji

1. Aktywuj okno aplikacji, które będzie odbierać naciśnięcia klawiszy, a następnie Wywołaj <xref:System.Windows.Forms.SendKeys.Send%2A> metodę lub <xref:System.Windows.Forms.SendKeys.SendWait%2A> . Ponieważ nie ma metody zarządzanej w celu aktywowania innej aplikacji, należy użyć natywnych metod systemu Windows, aby wymusić skupienie się na innych aplikacjach. Poniższy przykład kodu używa wywołania platformy, aby wywołać `FindWindow` metody i `SetForegroundWindow` uaktywnić okno aplikacji kalkulatora, a następnie wywołuje, <xref:System.Windows.Forms.SendKeys.SendWait%2A> Aby wystawić serię obliczeń w aplikacji Kalkulator.

    > [!NOTE]
    > Poprawne parametry `FindWindow` wywołania służącego do lokalizowania aplikacji kalkulatora różnią się w zależności od używanej wersji systemu Windows.  Poniższy kod umożliwia znalezienie aplikacji Kalkulator w systemie Windows 7. W systemie Windows Vista Zmień pierwszy parametr na "SciCalc". Aby określić poprawne parametry, można użyć narzędzia Spy + + dołączonego do programu Visual Studio.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a>Przykład

Poniższy przykład kodu jest kompletną aplikacją dla poprzedniego przykładu kodu.

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.

## <a name="see-also"></a>Zobacz też

- [Dane użytkownika w formularzach systemu Windows](user-input-in-windows-forms.md)
