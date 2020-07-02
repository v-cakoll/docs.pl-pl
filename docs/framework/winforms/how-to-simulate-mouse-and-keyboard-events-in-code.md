---
title: 'Instrukcje: Symulowanie zdarzeń myszy i klawiatury w kodzie'
description: Dowiedz się, jak używać opcji Windows Forms zapewnia programistyczne symulowanie danych wejściowych myszy i klawiatury.
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
ms.openlocfilehash: 3c60533479352151ac4f28690413ebc7d8e5879d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619250"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="6fa8f-103">Instrukcje: Symulowanie zdarzeń myszy i klawiatury w kodzie</span><span class="sxs-lookup"><span data-stu-id="6fa8f-103">How to: Simulate Mouse and Keyboard Events in Code</span></span>

<span data-ttu-id="6fa8f-104">Windows Forms oferuje kilka opcji programistycznego symulowania danych wejściowych myszy i klawiatury.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-104">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="6fa8f-105">Ten temat zawiera omówienie tych opcji.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-105">This topic provides an overview of these options.</span></span>

## <a name="simulating-mouse-input"></a><span data-ttu-id="6fa8f-106">Symulowanie danych wejściowych myszy</span><span class="sxs-lookup"><span data-stu-id="6fa8f-106">Simulating Mouse Input</span></span>

<span data-ttu-id="6fa8f-107">Najlepszym sposobem symulowania zdarzeń myszy jest wywołanie `On` metody *EventName* , która wywołuje zdarzenie myszy, które ma zostać symulowane.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-107">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="6fa8f-108">Ta opcja jest zazwyczaj możliwa tylko w kontrolkach niestandardowych i formularzach, ponieważ metody, które powodują wygenerowanie zdarzeń, są chronione i nie można uzyskać do nich dostępu poza formantem lub formularzem.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-108">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="6fa8f-109">Na przykład poniższe kroki ilustrują sposób symulowania kliknięcia prawego przycisku myszy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-109">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>

#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="6fa8f-110">Aby programowo kliknąć prawym przyciskiem myszy</span><span class="sxs-lookup"><span data-stu-id="6fa8f-110">To programmatically click the right mouse button</span></span>

1. <span data-ttu-id="6fa8f-111">Utwórz <xref:System.Windows.Forms.MouseEventArgs> Właściwość, której <xref:System.Windows.Forms.MouseEventArgs.Button%2A> właściwości jest ustawiona na <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> wartość.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-111">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>

2. <span data-ttu-id="6fa8f-112">Wywołaj <xref:System.Windows.Forms.Control.OnMouseClick%2A> metodę, używając <xref:System.Windows.Forms.MouseEventArgs> jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-112">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>

<span data-ttu-id="6fa8f-113">Aby uzyskać więcej informacji na temat kontrolek niestandardowych, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](./controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="6fa8f-113">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](./controls/developing-windows-forms-controls-at-design-time.md).</span></span>

<span data-ttu-id="6fa8f-114">Istnieją inne sposoby symulowania danych wejściowych myszy.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-114">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="6fa8f-115">Na przykład można programowo ustawić właściwość kontrolki, która reprezentuje stan, który jest zazwyczaj ustawiany za pomocą danych wejściowych myszy (takich jak <xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość <xref:System.Windows.Forms.CheckBox> kontrolki), lub bezpośrednio wywołać delegata, który jest dołączony do zdarzenia, które ma zostać symulowane.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-115">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>

## <a name="simulating-keyboard-input"></a><span data-ttu-id="6fa8f-116">Symulowanie danych wejściowych z klawiatury</span><span class="sxs-lookup"><span data-stu-id="6fa8f-116">Simulating Keyboard Input</span></span>

<span data-ttu-id="6fa8f-117">Chociaż można symulować dane wejściowe z klawiatury przy użyciu strategii omówionych powyżej dla danych wejściowych myszy, Windows Forms udostępnia również <xref:System.Windows.Forms.SendKeys> klasę do wysyłania naciśnięć klawiszy do aktywnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-117">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>

> [!CAUTION]
> <span data-ttu-id="6fa8f-118">Jeśli aplikacja jest przeznaczona do użytku międzynarodowego z różnymi klawiaturami, użycie <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> może dać nieprzewidywalne wyniki i należy je unikać.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-118">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>

> [!NOTE]
> <span data-ttu-id="6fa8f-119"><xref:System.Windows.Forms.SendKeys>Klasa została zaktualizowana dla .NET Framework 3,0, aby umożliwić jej używanie w aplikacjach uruchamianych w systemie Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-119">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="6fa8f-120">Ulepszone zabezpieczenia systemu Windows Vista (nazywanego kontrolą konta użytkownika lub UAC) uniemożliwiają działanie poprzedniej implementacji zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-120">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>
>
> <span data-ttu-id="6fa8f-121"><xref:System.Windows.Forms.SendKeys>Klasa jest podatna na problemy z chronometrażem, w przypadku których niektórzy deweloperzy musieli obejść.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-121">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="6fa8f-122">Zaktualizowana implementacja jest nadal podatna na problemy z chronometrażem, ale jest nieco szybsza i może wymagać wprowadzenia zmian w obejść.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-122">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="6fa8f-123"><xref:System.Windows.Forms.SendKeys>Klasa spróbuje najpierw użyć poprzedniej implementacji, a jeśli to się nie powiedzie, użyje nowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-123">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="6fa8f-124">W związku z tym <xref:System.Windows.Forms.SendKeys> Klasa może zachowywać się inaczej w różnych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-124">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="6fa8f-125">Ponadto, gdy <xref:System.Windows.Forms.SendKeys> Klasa używa nowej implementacji, <xref:System.Windows.Forms.SendKeys.SendWait%2A> Metoda nie będzie czekać na przetwarzanie komunikatów, gdy są wysyłane do innego procesu.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-125">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>
>
> <span data-ttu-id="6fa8f-126">Jeśli aplikacja korzysta ze spójności spójnej niezależnie od systemu operacyjnego, można wymusić, <xref:System.Windows.Forms.SendKeys> Aby Klasa korzystała z nowej implementacji, dodając do pliku app.config następujące ustawienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-126">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> <span data-ttu-id="6fa8f-127">Aby wymusić <xref:System.Windows.Forms.SendKeys> użycie poprzedniej implementacji przez klasę, użyj `"JournalHook"` zamiast niej wartości.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-127">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>

#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="6fa8f-128">Aby wysłać naciśnięcie klawisza do tej samej aplikacji</span><span class="sxs-lookup"><span data-stu-id="6fa8f-128">To send a keystroke to the same application</span></span>

1. <span data-ttu-id="6fa8f-129">Wywoływanie <xref:System.Windows.Forms.SendKeys.Send%2A> <xref:System.Windows.Forms.SendKeys.SendWait%2A> metody lub <xref:System.Windows.Forms.SendKeys> klasy.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-129">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="6fa8f-130">Określone nacionięcia klawiszy zostaną odebrane przez aktywną kontrolę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-130">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="6fa8f-131">Poniższy przykład kodu używa <xref:System.Windows.Forms.SendKeys.Send%2A> do symulowania naciskania klawisza ENTER, gdy użytkownik kliknie dwukrotnie powierzchnię formularza.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-131">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="6fa8f-132">W tym przykładzie przyjęto założenie, <xref:System.Windows.Forms.Form> że z pojedynczym <xref:System.Windows.Forms.Button> formantem ma indeks karty równy 0.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-132">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="6fa8f-133">Aby wysłać naciśnięcie klawisza do innej aplikacji</span><span class="sxs-lookup"><span data-stu-id="6fa8f-133">To send a keystroke to a different application</span></span>

1. <span data-ttu-id="6fa8f-134">Aktywuj okno aplikacji, które będzie odbierać naciśnięcia klawiszy, a następnie Wywołaj <xref:System.Windows.Forms.SendKeys.Send%2A> metodę lub <xref:System.Windows.Forms.SendKeys.SendWait%2A> .</span><span class="sxs-lookup"><span data-stu-id="6fa8f-134">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="6fa8f-135">Ponieważ nie ma metody zarządzanej w celu aktywowania innej aplikacji, należy użyć natywnych metod systemu Windows, aby wymusić skupienie się na innych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-135">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="6fa8f-136">Poniższy przykład kodu używa wywołania platformy, aby wywołać `FindWindow` metody i `SetForegroundWindow` uaktywnić okno aplikacji kalkulatora, a następnie wywołuje, <xref:System.Windows.Forms.SendKeys.SendWait%2A> Aby wystawić serię obliczeń w aplikacji Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-136">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fa8f-137">Poprawne parametry `FindWindow` wywołania służącego do lokalizowania aplikacji kalkulatora różnią się w zależności od używanej wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-137">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="6fa8f-138">Poniższy kod umożliwia znalezienie aplikacji Kalkulator w systemie Windows 7.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-138">The following code finds the Calculator application on Windows 7.</span></span> <span data-ttu-id="6fa8f-139">W systemie Windows Vista Zmień pierwszy parametr na "SciCalc".</span><span class="sxs-lookup"><span data-stu-id="6fa8f-139">On Windows Vista, change the first parameter to "SciCalc".</span></span> <span data-ttu-id="6fa8f-140">Aby określić poprawne parametry, można użyć narzędzia Spy + + dołączonego do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-140">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a><span data-ttu-id="6fa8f-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fa8f-141">Example</span></span>

<span data-ttu-id="6fa8f-142">Poniższy przykład kodu jest kompletną aplikacją dla poprzedniego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-142">The following code example is the complete application for the previous code examples.</span></span>

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="6fa8f-143">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6fa8f-143">Compiling the Code</span></span>

<span data-ttu-id="6fa8f-144">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6fa8f-144">This example requires:</span></span>

- <span data-ttu-id="6fa8f-145">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="6fa8f-145">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fa8f-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fa8f-146">See also</span></span>

- [<span data-ttu-id="6fa8f-147">Dane użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6fa8f-147">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
