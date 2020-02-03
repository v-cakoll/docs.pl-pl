---
title: Reagowanie na zmiany schematu czcionek w aplikacji Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739230"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="04dd1-102">Porady: reagowanie na zmiany schematu czcionek w aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04dd1-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="04dd1-103">W systemach operacyjnych Windows, użytkownik może zmienić ustawienia czcionek dla całego systemu, aby czcionka domyślna była większa lub mniejsza.</span><span class="sxs-lookup"><span data-stu-id="04dd1-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="04dd1-104">Zmiana tych ustawień czcionki jest niezwykle ważna dla użytkowników, którzy są wizualnie niepełnosprawni i wymagają większego typu w celu odczytania tekstu na ekranie.</span><span class="sxs-lookup"><span data-stu-id="04dd1-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="04dd1-105">Możesz dostosować aplikację Windows Forms, aby reagować na te zmiany, zwiększając lub zmniejszając rozmiar formularza i cały tekst zawarty po każdym zmianie schematu czcionek.</span><span class="sxs-lookup"><span data-stu-id="04dd1-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="04dd1-106">Jeśli chcesz, aby formularz dynamicznie mieścił zmiany rozmiarów czcionek, możesz dodać kod do formularza.</span><span class="sxs-lookup"><span data-stu-id="04dd1-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="04dd1-107">Zazwyczaj domyślną czcionką używaną przez Windows Forms jest czcionka zwrócona przez wywołanie przestrzeni nazw <xref:Microsoft.Win32> do `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="04dd1-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="04dd1-108">Czcionka zwracana przez to wywołanie zmienia się tylko wtedy, gdy zmienia się rozdzielczość ekranu.</span><span class="sxs-lookup"><span data-stu-id="04dd1-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="04dd1-109">Jak pokazano w poniższej procedurze, kod musi zmienić czcionkę domyślną, aby <xref:System.Drawing.SystemFonts.IconTitleFont%2A>, aby odpowiadały na zmiany rozmiaru czcionki.</span><span class="sxs-lookup"><span data-stu-id="04dd1-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="04dd1-110">Aby używać czcionki pulpitu i odpowiadać na zmiany schematu czcionek</span><span class="sxs-lookup"><span data-stu-id="04dd1-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1. <span data-ttu-id="04dd1-111">Utwórz formularz i Dodaj do niego formanty.</span><span class="sxs-lookup"><span data-stu-id="04dd1-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="04dd1-112">Aby uzyskać więcej informacji, zobacz [How to: Create a Windows Forms Application z wiersza polecenia](how-to-create-a-windows-forms-application-from-the-command-line.md) i [formantów, które mają być używane w Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="04dd1-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="04dd1-113">Dodaj odwołanie do przestrzeni nazw <xref:Microsoft.Win32> do kodu.</span><span class="sxs-lookup"><span data-stu-id="04dd1-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="04dd1-114">Dodaj następujący kod do konstruktora formularza, aby podłączyć wymagane programy obsługi zdarzeń i zmienić domyślną czcionkę używaną dla formularza.</span><span class="sxs-lookup"><span data-stu-id="04dd1-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="04dd1-115">Zaimplementuj procedurę obsługi dla zdarzenia <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>, które powoduje automatyczne skalowanie formularza po zmianie kategorii <xref:Microsoft.Win32.UserPreferenceCategory.Window>.</span><span class="sxs-lookup"><span data-stu-id="04dd1-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. <span data-ttu-id="04dd1-116">Na koniec Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.FormClosing>, które odłącza procedurę obsługi zdarzeń <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="04dd1-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="04dd1-117">Niepowodzenie dołączenia tego kodu spowoduje przeciek pamięci przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="04dd1-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. <span data-ttu-id="04dd1-118">Kompiluj i uruchamiaj kod.</span><span class="sxs-lookup"><span data-stu-id="04dd1-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="04dd1-119">Aby ręcznie zmienić schemat czcionek w systemie Windows XP</span><span class="sxs-lookup"><span data-stu-id="04dd1-119">To manually change the font scheme in Windows XP</span></span>  
  
1. <span data-ttu-id="04dd1-120">Gdy aplikacja Windows Forms jest uruchomiona, kliknij prawym przyciskiem myszy pulpit systemu Windows i wybierz polecenie **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="04dd1-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="04dd1-121">W oknie dialogowym **właściwości wyświetlania** kliknij kartę **wygląd** .</span><span class="sxs-lookup"><span data-stu-id="04dd1-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3. <span data-ttu-id="04dd1-122">W polu listy rozwijanej **rozmiar czcionki** wybierz nowy rozmiar czcionki.</span><span class="sxs-lookup"><span data-stu-id="04dd1-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="04dd1-123">Zobaczysz, że formularz teraz reaguje na zmiany w czasie wykonywania w schemacie czcionek pulpitu.</span><span class="sxs-lookup"><span data-stu-id="04dd1-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="04dd1-124">Gdy użytkownik zmieni się między **normalną**, **dużą czcionką**i **bardzo dużą**czcionką, formularz zmienia czcionkę i skaluje się poprawnie.</span><span class="sxs-lookup"><span data-stu-id="04dd1-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04dd1-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="04dd1-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="04dd1-126">Konstruktor w tym przykładzie kodu zawiera wywołanie do `InitializeComponent`, który jest definiowany podczas tworzenia nowego projektu Windows Forms w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="04dd1-126">The constructor in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="04dd1-127">Usuń ten wiersz kodu, jeśli tworzysz aplikację w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="04dd1-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04dd1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04dd1-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="04dd1-129">Automatyczne skalowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04dd1-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
