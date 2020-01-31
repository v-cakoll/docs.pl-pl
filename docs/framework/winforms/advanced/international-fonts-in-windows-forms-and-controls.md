---
title: Międzynarodowe czcionki w formularzach i kontrolkach
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 59dde6bb384d644321a8ff5674d735f8e6d36fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743521"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="c33ae-102">Międzynarodowe czcionki w Windows Forms i kontrolki</span><span class="sxs-lookup"><span data-stu-id="c33ae-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="c33ae-103">W aplikacjach międzynarodowych zalecaną metodą wybierania czcionek jest użycie opcji powrotu do czcionki wszędzie tam, gdzie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="c33ae-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="c33ae-104">Powrót do czcionki oznacza, że system Określa, do jakiego skryptu należy znak.</span><span class="sxs-lookup"><span data-stu-id="c33ae-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="c33ae-105">Używanie powrotu do czcionek</span><span class="sxs-lookup"><span data-stu-id="c33ae-105">Using font fallback</span></span>

<span data-ttu-id="c33ae-106">Aby skorzystać z tej funkcji, nie ustawiaj właściwości <xref:System.Drawing.Font> dla formularza ani innego elementu.</span><span class="sxs-lookup"><span data-stu-id="c33ae-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="c33ae-107">Aplikacja automatycznie użyje domyślnej czcionki systemowej, która różni się od jednego zlokalizowanego języka systemu operacyjnego do innego.</span><span class="sxs-lookup"><span data-stu-id="c33ae-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="c33ae-108">Gdy aplikacja zostanie uruchomiona, system automatycznie poda poprawną czcionkę dla kultury wybranej w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="c33ae-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="c33ae-109">Istnieje wyjątek od reguły, która nie ustawia czcionki, która umożliwia zmianę stylu czcionki.</span><span class="sxs-lookup"><span data-stu-id="c33ae-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="c33ae-110">Może to być ważne w przypadku aplikacji, w której użytkownik klika przycisk, aby tekst w polu tekstowym był wyświetlany jako pogrubiony.</span><span class="sxs-lookup"><span data-stu-id="c33ae-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="c33ae-111">W tym celu należy napisać funkcję, aby zmienić styl czcionki pola tekstowego na pogrubioną, w zależności od rodzaju czcionki formularza.</span><span class="sxs-lookup"><span data-stu-id="c33ae-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="c33ae-112">Ważne jest, aby wywołać tę funkcję w dwóch miejscach: w obsłudze zdarzeń <xref:System.Windows.Forms.Control.Click> przycisku i w obsłudze zdarzeń <xref:System.Windows.Forms.Control.FontChanged>.</span><span class="sxs-lookup"><span data-stu-id="c33ae-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="c33ae-113">Jeśli funkcja jest wywoływana tylko w programie obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> i niektóre inne fragmenty kodu zmieniają rodzinę czcionek całego formularza, pole tekstowe nie zmieni się w resztę formularza.</span><span class="sxs-lookup"><span data-stu-id="c33ae-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

<span data-ttu-id="c33ae-114">Jednak podczas lokalizowania aplikacji czcionka pogrubiona może być wyświetlana w niewłaściwy sposób w przypadku niektórych języków.</span><span class="sxs-lookup"><span data-stu-id="c33ae-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="c33ae-115">Jeśli jest to problem, chcemy, aby lokalizatory miały możliwość przełączania czcionki z pogrubionej do zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="c33ae-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="c33ae-116">Ponieważ lokalizatory zazwyczaj nie są deweloperami i nie mają dostępu do kodu źródłowego, tylko w przypadku plików zasobów, ta opcja musi być ustawiona w plikach zasobów.</span><span class="sxs-lookup"><span data-stu-id="c33ae-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="c33ae-117">W tym celu należy ustawić właściwość <xref:System.Drawing.Font.Bold%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="c33ae-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="c33ae-118">Powoduje to zapisanie ustawienia czcionki do plików zasobów, gdzie lokalizatory mogą go edytować.</span><span class="sxs-lookup"><span data-stu-id="c33ae-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="c33ae-119">Następnie napiszesz kod po metodzie `InitializeComponent`, aby zresetować czcionkę w oparciu o zawartość czcionki formularza, ale przy użyciu stylu czcionki określonego w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="c33ae-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="c33ae-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c33ae-120">See also</span></span>

- [<span data-ttu-id="c33ae-121">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="c33ae-121">Using Fonts and Text</span></span>](using-fonts-and-text.md)
