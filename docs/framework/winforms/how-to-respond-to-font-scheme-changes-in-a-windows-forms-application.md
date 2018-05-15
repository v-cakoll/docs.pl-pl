---
title: 'Porady: reagowanie na zmiany schematu czcionek w aplikacji Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 455609ea602f450803718f5be34618b087560d21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="d6fac-102">Porady: reagowanie na zmiany schematu czcionek w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6fac-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="d6fac-103">W systemach operacyjnych Windows użytkownik może zmienić ustawienia czcionki systemowe, aby upewnić domyślnej czcionki są wyświetlane, większy lub mniejszy.</span><span class="sxs-lookup"><span data-stu-id="d6fac-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="d6fac-104">Zmiana tych ustawień czcionki jest kluczowa dla użytkowników, którzy są niedowidzących i wymagają większej typu tekstu na ekranie.</span><span class="sxs-lookup"><span data-stu-id="d6fac-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="d6fac-105">Można dostosować aplikacji Windows Forms reagowanie na te zmiany, zwiększ lub Zmniejsz rozmiar formularza i wszystkich zawartych w niej tekstu przy każdej zmianie schematu czcionek.</span><span class="sxs-lookup"><span data-stu-id="d6fac-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="d6fac-106">Jeśli chcesz, aby formularz, aby uwzględnić zmiany w rozmiarze czcionki dynamicznie, można dodać kod do formularza.</span><span class="sxs-lookup"><span data-stu-id="d6fac-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="d6fac-107">Zazwyczaj domyślnej czcionki używanej przez formularze systemu Windows jest czcionki zwrócony przez <xref:Microsoft.Win32> wywołanie przestrzeni nazw `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="d6fac-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="d6fac-108">Czcionki zwróconych przez to połączenie zostanie zmieniona tylko, gdy zmienia się rozdzielczość ekranu.</span><span class="sxs-lookup"><span data-stu-id="d6fac-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="d6fac-109">Jak pokazano w poniższej procedurze, kod należy zmienić domyślną czcionkę do <xref:System.Drawing.SystemFonts.IconTitleFont%2A> na odpowiadanie na zmiany w rozmiarze czcionki.</span><span class="sxs-lookup"><span data-stu-id="d6fac-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="d6fac-110">Użyj czcionki pulpitu i reagowanie na zmiany schematu czcionek</span><span class="sxs-lookup"><span data-stu-id="d6fac-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="d6fac-111">Tworzenie formularza i Dodaj formanty, które mają do niej.</span><span class="sxs-lookup"><span data-stu-id="d6fac-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="d6fac-112">Aby uzyskać więcej informacji, zobacz [porady: tworzenie aplikacji Windows Forms z wiersza polecenia](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) i [formanty do użycia w formularzach systemu Windows](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d6fac-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="d6fac-113">Dodaj odwołanie do <xref:Microsoft.Win32> przestrzeni nazw w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d6fac-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="d6fac-114">Dodaj następujący kod do konstruktora formularza dołączenie obsługi zdarzeń wymagane i zmienić domyślną czcionkę używany dla formularza.</span><span class="sxs-lookup"><span data-stu-id="d6fac-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="d6fac-115">Implementowanie obsługi dla <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzenie, które powoduje formularza, aby skalować automatycznie po <xref:Microsoft.Win32.UserPreferenceCategory.Window> zmian kategorii.</span><span class="sxs-lookup"><span data-stu-id="d6fac-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="d6fac-116">Na koniec implementuje obsługi dla <xref:System.Windows.Forms.Form.FormClosing> zdarzenie, które odłącza <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d6fac-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d6fac-117">Nie można dołączyć ten kod spowoduje, że aplikacja do wycieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="d6fac-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  <span data-ttu-id="d6fac-118">Kompilowanie i uruchamianie kodu.</span><span class="sxs-lookup"><span data-stu-id="d6fac-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="d6fac-119">Aby ręcznie zmienić schematu czcionek w systemie Windows XP</span><span class="sxs-lookup"><span data-stu-id="d6fac-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="d6fac-120">Po uruchomieniu aplikacji formularzy systemu Windows kliknij prawym przyciskiem myszy na pulpicie systemu Windows i wybierz polecenie **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="d6fac-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="d6fac-121">W **właściwości wyświetlania** okno dialogowe, kliknij przycisk **wygląd** kartę.</span><span class="sxs-lookup"><span data-stu-id="d6fac-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="d6fac-122">Z **rozmiar czcionki** listy rozwijanej wybierz nowy rozmiar czcionki.</span><span class="sxs-lookup"><span data-stu-id="d6fac-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="d6fac-123">Można zauważyć, że formularz teraz reaguje na Uruchom czasu zmiany schematu czcionek pulpitu.</span><span class="sxs-lookup"><span data-stu-id="d6fac-123">You will notice that the form now reacts to run time changes in the desktop font scheme.</span></span> <span data-ttu-id="d6fac-124">Gdy użytkownik zmieni się między **normalny**, **duże czcionki**, i **dodatkowe duże czcionki**, formularz zmiany czcionki i skaluje poprawnie.</span><span class="sxs-lookup"><span data-stu-id="d6fac-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6fac-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6fac-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="d6fac-126">Constructer w tym przykładzie kodu zawiera wywołanie `InitializeComponent`, który jest zdefiniowany podczas tworzenia nowego projektu Windows Forms w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6fac-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="d6fac-127">Usuń ten wiersz kodu, jeśli tworzysz aplikację w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d6fac-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fac-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6fac-128">See Also</span></span>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [<span data-ttu-id="d6fac-129">Automatyczne skalowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6fac-129">Automatic Scaling in Windows Forms</span></span>](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
