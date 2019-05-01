---
title: Międzynarodowe czcionki w formularzach Windows i kontrolek
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
ms.openlocfilehash: 1f9afd575e2de04e0b11556ad34436839e13d968
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942899"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="fdf14-102">Międzynarodowe czcionki w formularzach Windows i kontrolek</span><span class="sxs-lookup"><span data-stu-id="fdf14-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="fdf14-103">W aplikacjach międzynarodowych wybierania czcionek zaleca się użyć rezerwa czcionek, tam gdzie to możliwe.</span><span class="sxs-lookup"><span data-stu-id="fdf14-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="fdf14-104">Czcionka rezerwowego oznacza, że system określi, co skrypt znak należy do.</span><span class="sxs-lookup"><span data-stu-id="fdf14-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="fdf14-105">Przy użyciu czcionki rezerwowe</span><span class="sxs-lookup"><span data-stu-id="fdf14-105">Using font fallback</span></span>

<span data-ttu-id="fdf14-106">Aby móc korzystać z tej funkcji, nie należy ustawiać <xref:System.Drawing.Font> właściwości dla formularza lub innego elementu.</span><span class="sxs-lookup"><span data-stu-id="fdf14-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="fdf14-107">Aplikacja będzie automatycznie używać domyślnej czcionki systemowej, która różni się od jednego zlokalizowanego języka systemu operacyjnego do innego.</span><span class="sxs-lookup"><span data-stu-id="fdf14-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="fdf14-108">Gdy aplikacja zostanie uruchomiona, system automatycznie zapewnić poprawną czcionkę dla kultury wybrane w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="fdf14-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="fdf14-109">Występuje wyjątek do reguły nie ustawienia czcionki, której dotyczy zmiana styl czcionki.</span><span class="sxs-lookup"><span data-stu-id="fdf14-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="fdf14-110">Może to być ważne dla aplikacji, w którym użytkownik kliknie przycisk, aby tekst w polu tekstowym, są wyświetlane pogrubioną czcionką.</span><span class="sxs-lookup"><span data-stu-id="fdf14-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="fdf14-111">Aby to zrobić, należy napisać funkcję, aby zmienić styl czcionki pole tekstowe do pogrubienie, oparciu o dowolnej formie czcionki.</span><span class="sxs-lookup"><span data-stu-id="fdf14-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="fdf14-112">Ważne jest, aby wywołać tę funkcję w dwóch miejscach: przycisku <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń i <xref:System.Windows.Forms.Control.FontChanged> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fdf14-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="fdf14-113">Jeśli funkcja jest wywoływana tylko w <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń i innych fragment kodu zmienia rodzinę czcionek cały formularz, pole tekstowe nie zmienia się w pozostałej części formularza.</span><span class="sxs-lookup"><span data-stu-id="fdf14-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

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

<span data-ttu-id="fdf14-114">Jednak gdy możesz zlokalizować aplikację, pogrubioną czcionką mogą być wyświetlane nieprawidłowo w przypadku niektórych języków.</span><span class="sxs-lookup"><span data-stu-id="fdf14-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="fdf14-115">Jeśli jest to niepożądane, chcesz lokalizatorzy dostępna będzie opcja przełączania czcionki pogrubioną czcionką na zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="fdf14-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="fdf14-116">Ponieważ lokalizatorzy nie są zwykle deweloperzy i nie mają dostępu do kodu źródłowego, tylko do plików zasobów, ta opcja musi być ustawiona w plikach zasobów.</span><span class="sxs-lookup"><span data-stu-id="fdf14-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="fdf14-117">Aby to zrobić, należy ustawić <xref:System.Drawing.Font.Bold%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="fdf14-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="fdf14-118">Powoduje to ustawienie czcionki, są zapisywane w plikach zasobów, w którym lokalizatorzy można go edytować.</span><span class="sxs-lookup"><span data-stu-id="fdf14-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="fdf14-119">Następnie napisać kod po `InitializeComponent` metodę, aby zresetować czcionki na podstawie informacji o dowolnej formie czcionki, ale za pomocą styl czcionki określonych w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="fdf14-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="fdf14-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdf14-120">See also</span></span>

- [<span data-ttu-id="fdf14-121">Globalizowanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fdf14-121">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
- [<span data-ttu-id="fdf14-122">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="fdf14-122">Using Fonts and Text</span></span>](using-fonts-and-text.md)
