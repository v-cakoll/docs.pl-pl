---
title: 'Instrukcje: Reagowanie na zmiany schematu czcionek w aplikacji Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 85770687ecfad690a251eafec9051c4c20f45dd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182107"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="e5d77-102">Instrukcje: Reagowanie na zmiany schematu czcionek w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5d77-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="e5d77-103">W systemach operacyjnych Windows użytkownik może zmienić ustawień czcionki systemowe, aby były domyślną czcionkę, są wyświetlane, większy lub mniejszy.</span><span class="sxs-lookup"><span data-stu-id="e5d77-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="e5d77-104">Zmiana tych ustawień Czcionka jest krytyczny dla użytkowników, którzy niedowidzących i wymagają większej typu do odczytywania tekstu na swoich ekranach.</span><span class="sxs-lookup"><span data-stu-id="e5d77-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="e5d77-105">Można dostosować aplikację Windows Forms, aby reagować na te zmiany przez zwiększenie lub zmniejszenie rozmiaru formularza i wszystkie zawarte tekstu, zawsze wtedy, gdy zmiany schematu czcionek.</span><span class="sxs-lookup"><span data-stu-id="e5d77-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="e5d77-106">Jeśli chcesz, aby formularza w taki sposób, aby uwzględnić zmiany w rozmiary czcionek dynamicznie, można dodać kod do formularza.</span><span class="sxs-lookup"><span data-stu-id="e5d77-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="e5d77-107">Zazwyczaj domyślna czcionka używanych przez formularze Windows jest czcionki zwrócony przez <xref:Microsoft.Win32> wywołanie przestrzeni nazw `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="e5d77-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="e5d77-108">Czcionka zwróconych przez to wywołanie zmienia tylko po zmianie rozdzielczość ekranu.</span><span class="sxs-lookup"><span data-stu-id="e5d77-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="e5d77-109">Jak pokazano w poniższej procedurze, kod musi zmienić domyślną czcionkę do <xref:System.Drawing.SystemFonts.IconTitleFont%2A> do reagowania na zmiany rozmiaru czcionki.</span><span class="sxs-lookup"><span data-stu-id="e5d77-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="e5d77-110">Użyj czcionki pulpitu i reagować na zmiany schematu czcionek</span><span class="sxs-lookup"><span data-stu-id="e5d77-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="e5d77-111">Tworzenie formularza i dodać kontrolki, które mają do niego.</span><span class="sxs-lookup"><span data-stu-id="e5d77-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="e5d77-112">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie aplikacji programu Windows Forms z wiersza polecenia](how-to-create-a-windows-forms-application-from-the-command-line.md) i [kontrolki do użycia w formularzach Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e5d77-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="e5d77-113">Dodaj odwołanie do <xref:Microsoft.Win32> przestrzeni nazw w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e5d77-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="e5d77-114">Dodaj następujący kod do konstruktora formularza można dołączyć procedury obsługi zdarzeń wymagane i zmieniać domyślną czcionkę używaną do formularza.</span><span class="sxs-lookup"><span data-stu-id="e5d77-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="e5d77-115">Implementowanie obsługi dla <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń, który powoduje, że formularza w celu automatycznego skalowania podczas <xref:Microsoft.Win32.UserPreferenceCategory.Window> zmian kategorii.</span><span class="sxs-lookup"><span data-stu-id="e5d77-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="e5d77-116">Na koniec zaimplementować funkcję obsługi <xref:System.Windows.Forms.Form.FormClosing> zdarzenia, które powoduje odłączenie <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e5d77-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="e5d77-117">Niepodanie tego kodu spowoduje, że aplikacja do wycieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="e5d77-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6.  <span data-ttu-id="e5d77-118">Skompiluj i uruchom kod.</span><span class="sxs-lookup"><span data-stu-id="e5d77-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="e5d77-119">Aby ręcznie zmienić schematu czcionek w Windows XP</span><span class="sxs-lookup"><span data-stu-id="e5d77-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="e5d77-120">Po uruchomieniu aplikacji Windows Forms kliknij prawym przyciskiem myszy na pulpit Windows i wybierz polecenie **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="e5d77-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e5d77-121">W **właściwości wyświetlania** okno dialogowe, kliknij przycisk **wygląd** kartę.</span><span class="sxs-lookup"><span data-stu-id="e5d77-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="e5d77-122">Z **rozmiar czcionki** listy rozwijanej wybierz nowy rozmiar czcionki.</span><span class="sxs-lookup"><span data-stu-id="e5d77-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="e5d77-123">Można zauważyć, że formularz teraz w przypadku środowiska wykonawczego zmiany schematu czcionek pulpitu.</span><span class="sxs-lookup"><span data-stu-id="e5d77-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="e5d77-124">Gdy użytkownik zmieni się między **normalny**, **duży rozmiar czcionki**, i **dodatkowe duży rozmiar czcionki**, formularz zmieni się czcionka i skaluje się poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e5d77-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5d77-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5d77-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="e5d77-126">Constructer w tym przykładzie kod zawiera wywołanie `InitializeComponent`, który jest zdefiniowany, tworząc nowy projekt Windows Forms w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5d77-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="e5d77-127">Usuń ten wiersz kodu, jeśli tworzysz aplikację w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5d77-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d77-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5d77-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="e5d77-129">Automatyczne skalowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e5d77-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
