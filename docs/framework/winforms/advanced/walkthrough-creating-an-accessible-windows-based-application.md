---
title: 'Przewodnik: Tworzenie dostępnej aplikacji opartej na systemie Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
dev_langs:
- csharp
- vb
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: b8f0c7c4584505d382e78aca68e2e99c9fa7748f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834631"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="833c6-102">Przewodnik: Tworzenie dostępnej aplikacji opartej na systemie Windows</span><span class="sxs-lookup"><span data-stu-id="833c6-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>

<span data-ttu-id="833c6-103">Tworzenie dostępnej aplikacji ma istotne znaczenie biznesowe.</span><span class="sxs-lookup"><span data-stu-id="833c6-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="833c6-104">Wiele rządów ma regulacje dotyczące ułatwień dostępu do zakupu oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="833c6-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="833c6-105">Logo certyfikowane dla systemu Windows zawiera wymagania dotyczące ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="833c6-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="833c6-106">W przypadku, gdy wszyscy potencjalni klienci mają wpływ na 30 000 000y, mogą oni uzyskać dostęp do oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="833c6-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>

<span data-ttu-id="833c6-107">Ten przewodnik dotyczy pięciu wymagań dotyczących ułatwień dostępu dla logo certyfikowane dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="833c6-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="833c6-108">Zgodnie z tymi wymaganiami dostępna aplikacja będzie:</span><span class="sxs-lookup"><span data-stu-id="833c6-108">According to these requirements, an accessible application will:</span></span>

- <span data-ttu-id="833c6-109">Obsługa rozmiaru panelu sterowania, koloru, czcionki i ustawień wejściowych.</span><span class="sxs-lookup"><span data-stu-id="833c6-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="833c6-110">Pasek menu, pasek tytułu, obramowania i pasek stanu będą wszystkie zmiany rozmiaru, gdy użytkownik zmieni ustawienia panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="833c6-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="833c6-111">W tej aplikacji nie są wymagane żadne dodatkowe zmiany w kontrolkach lub kodzie.</span><span class="sxs-lookup"><span data-stu-id="833c6-111">No additional changes to the controls or code are required in this application.</span></span>

- <span data-ttu-id="833c6-112">Duży kontrast tryb obsługi.</span><span class="sxs-lookup"><span data-stu-id="833c6-112">Support High Contrast mode.</span></span>

- <span data-ttu-id="833c6-113">Zapewnianie udokumentowanego dostępu klawiaturowego do wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="833c6-113">Provide documented keyboard access to all features.</span></span>

- <span data-ttu-id="833c6-114">Uwidocznij lokalizację fokusu klawiatury wizualnie i programowo.</span><span class="sxs-lookup"><span data-stu-id="833c6-114">Expose location of the keyboard focus visually and programmatically.</span></span>

- <span data-ttu-id="833c6-115">Unikaj samodzielnego przekazywania ważnych informacji.</span><span class="sxs-lookup"><span data-stu-id="833c6-115">Avoid conveying important information by sound alone.</span></span>

<span data-ttu-id="833c6-116">Aby uzyskać więcej informacji, zobacz [zasoby dotyczące projektowania dostępnych aplikacji](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="833c6-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>

<span data-ttu-id="833c6-117">Aby uzyskać informacje na temat obsługi różnych układów klawiatury, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych do użytku](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="833c6-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="833c6-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="833c6-118">Creating the Project</span></span>

<span data-ttu-id="833c6-119">W tym instruktażu tworzony jest interfejs użytkownika dla aplikacji, która przyjmuje zamówienia Pizza.</span><span class="sxs-lookup"><span data-stu-id="833c6-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="833c6-120">Składa się z <xref:System.Windows.Forms.TextBox> dla nazwy klienta, grupy <xref:System.Windows.Forms.RadioButton> do wybrania rozmiaru Pizza, <xref:System.Windows.Forms.CheckedListBox> do wybrania toppings, dwóch kontrolek z etykietą Order i Cancel oraz menu z poleceniem Exit.</span><span class="sxs-lookup"><span data-stu-id="833c6-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>

<span data-ttu-id="833c6-121">Użytkownik wprowadza nazwę klienta, rozmiar Pizza i żądany toppings.</span><span class="sxs-lookup"><span data-stu-id="833c6-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="833c6-122">Gdy użytkownik kliknie przycisk zamówienie, w oknie komunikatu zostanie wyświetlone podsumowanie zamówienia i jego koszt, a kontrolki są wyczyszczone i gotowe do kolejnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="833c6-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="833c6-123">Gdy użytkownik kliknie przycisk Anuluj, formanty są wyczyszczone i gotowe do kolejnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="833c6-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="833c6-124">Gdy użytkownik kliknie element menu Zakończ, program zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="833c6-124">When the user clicks the Exit menu item, the program closes.</span></span>

<span data-ttu-id="833c6-125">Nacisk tego instruktażu nie jest kodem dla systemu zamówień sprzedaży detalicznej, ale umożliwia dostęp do interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="833c6-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="833c6-126">W przewodniku przedstawiono funkcje ułatwień dostępu kilku często używanych kontrolek, w tym przyciski, przyciski radiowe, pola tekstowe i etykiety.</span><span class="sxs-lookup"><span data-stu-id="833c6-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>

#### <a name="to-begin-making-the-application"></a><span data-ttu-id="833c6-127">Aby rozpocząć tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="833c6-127">To begin making the application</span></span>

- <span data-ttu-id="833c6-128">Utwórz nową aplikację systemu Windows w Visual Basic lub wizualizacji C#.</span><span class="sxs-lookup"><span data-stu-id="833c6-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="833c6-129">Nazwij projekt **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="833c6-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="833c6-130">Aby uzyskać szczegółowe informacje, zobacz [Tworzenie nowych rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="833c6-130">For details, see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>

## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="833c6-131">Dodawanie kontrolek do formularza</span><span class="sxs-lookup"><span data-stu-id="833c6-131">Adding the Controls to the Form</span></span>

<span data-ttu-id="833c6-132">Podczas dodawania kontrolek do formularza należy wziąć pod uwagę następujące wytyczne, aby udostępnić dostępną aplikację:</span><span class="sxs-lookup"><span data-stu-id="833c6-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>

- <span data-ttu-id="833c6-133">Ustaw właściwości <xref:System.Windows.Forms.Control.AccessibleDescription%2A> i <xref:System.Windows.Forms.Control.AccessibleName%2A>.</span><span class="sxs-lookup"><span data-stu-id="833c6-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="833c6-134">W tym przykładzie jest to ustawienie domyślne dla <xref:System.Windows.Forms.Control.AccessibleRole%2A>.</span><span class="sxs-lookup"><span data-stu-id="833c6-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="833c6-135">Aby uzyskać więcej informacji na temat właściwości ułatwień dostępu, zobacz temat [zapewnianie informacji o ułatwieniach dostępu dla kontrolek w formularzu systemu Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="833c6-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>

- <span data-ttu-id="833c6-136">Ustaw rozmiar czcionki na 10 punktów lub większy.</span><span class="sxs-lookup"><span data-stu-id="833c6-136">Set the font size to 10 points or larger.</span></span>

  > [!NOTE]
  > <span data-ttu-id="833c6-137">Jeśli ustawisz rozmiar czcionki formularza na 10 po rozpoczęciu, wówczas wszystkie kontrolki dodane do formularza będą mieć rozmiar czcionki 10.</span><span class="sxs-lookup"><span data-stu-id="833c6-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>

- <span data-ttu-id="833c6-138">Upewnij się, że każda kontrolka etykieta opisująca kontrolkę TextBox bezpośrednio poprzedza formant TextBox w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="833c6-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>

- <span data-ttu-id="833c6-139">Dodaj klucz dostępu przy użyciu znaku "&" do właściwości <xref:System.Windows.Forms.Control.Text%2A> każdej kontrolki, do której użytkownik może chcieć przejść.</span><span class="sxs-lookup"><span data-stu-id="833c6-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>

- <span data-ttu-id="833c6-140">Dodaj klucz dostępu przy użyciu znaku "&" do właściwości <xref:System.Windows.Forms.Control.Text%2A> etykiety, która poprzedza kontrolkę, do której użytkownik może chcieć przejść.</span><span class="sxs-lookup"><span data-stu-id="833c6-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="833c6-141">Ustaw właściwość Labels "<xref:System.Windows.Forms.Label.UseMnemonic%2A>" na `true`, tak aby fokus został ustawiony na następną kontrolkę w kolejności tabulacji, gdy użytkownik naciśnie klawisz dostępu.</span><span class="sxs-lookup"><span data-stu-id="833c6-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>

- <span data-ttu-id="833c6-142">Dodaj klucze dostępu do wszystkich elementów menu.</span><span class="sxs-lookup"><span data-stu-id="833c6-142">Add access keys to all menu items.</span></span>

#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="833c6-143">Aby udostępnić aplikację systemu Windows</span><span class="sxs-lookup"><span data-stu-id="833c6-143">To make your Windows Application accessible</span></span>

- <span data-ttu-id="833c6-144">Dodaj kontrolki do formularza i ustaw właściwości zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="833c6-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="833c6-145">Zapoznaj się z obrazem na końcu tabeli, aby zapoznać się z modelem jak rozmieścić kontrolki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="833c6-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>

   |<span data-ttu-id="833c6-146">Obiekt</span><span class="sxs-lookup"><span data-stu-id="833c6-146">Object</span></span>|<span data-ttu-id="833c6-147">Właściwość</span><span class="sxs-lookup"><span data-stu-id="833c6-147">Property</span></span>|<span data-ttu-id="833c6-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="833c6-148">Value</span></span>|
   |------------|--------------|-----------|
   |<span data-ttu-id="833c6-149">Formularz</span><span class="sxs-lookup"><span data-stu-id="833c6-149">Form1</span></span>|<span data-ttu-id="833c6-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-150">AccessibleDescription</span></span>|<span data-ttu-id="833c6-151">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="833c6-151">Order form</span></span>|
   ||<span data-ttu-id="833c6-152">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-152">AccessibleName</span></span>|<span data-ttu-id="833c6-153">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="833c6-153">Order form</span></span>|
   ||<span data-ttu-id="833c6-154">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="833c6-154">Font Size</span></span>|<span data-ttu-id="833c6-155">10</span><span class="sxs-lookup"><span data-stu-id="833c6-155">10</span></span>|
   ||<span data-ttu-id="833c6-156">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-156">Text</span></span>|<span data-ttu-id="833c6-157">Formularz zamówienia Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-157">Pizza Order Form</span></span>|
   |<span data-ttu-id="833c6-158">Elemencie</span><span class="sxs-lookup"><span data-stu-id="833c6-158">PictureBox</span></span>|<span data-ttu-id="833c6-159">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-159">Name</span></span>|<span data-ttu-id="833c6-160">Znaku</span><span class="sxs-lookup"><span data-stu-id="833c6-160">logo</span></span>|
   ||<span data-ttu-id="833c6-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-161">AccessibleDescription</span></span>|<span data-ttu-id="833c6-162">Wycinek elementu Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-162">A slice of pizza</span></span>|
   ||<span data-ttu-id="833c6-163">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-163">AccessibleName</span></span>|<span data-ttu-id="833c6-164">Logo firmy</span><span class="sxs-lookup"><span data-stu-id="833c6-164">Company logo</span></span>|
   ||<span data-ttu-id="833c6-165">Image (Obraz)</span><span class="sxs-lookup"><span data-stu-id="833c6-165">Image</span></span>|<span data-ttu-id="833c6-166">Dowolna ikona lub mapa bitowa</span><span class="sxs-lookup"><span data-stu-id="833c6-166">Any icon or bitmap</span></span>|
   |<span data-ttu-id="833c6-167">Etykieta</span><span class="sxs-lookup"><span data-stu-id="833c6-167">Label</span></span>|<span data-ttu-id="833c6-168">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-168">Name</span></span>|<span data-ttu-id="833c6-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="833c6-169">companyLabel</span></span>|
   ||<span data-ttu-id="833c6-170">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-170">Text</span></span>|<span data-ttu-id="833c6-171">Dobre Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-171">Good Pizza</span></span>|
   ||<span data-ttu-id="833c6-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-172">TabIndex</span></span>|<span data-ttu-id="833c6-173">1</span><span class="sxs-lookup"><span data-stu-id="833c6-173">1</span></span>|
   ||<span data-ttu-id="833c6-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-174">AccessibleDescription</span></span>|<span data-ttu-id="833c6-175">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="833c6-175">Company name</span></span>|
   ||<span data-ttu-id="833c6-176">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-176">AccessibleName</span></span>|<span data-ttu-id="833c6-177">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="833c6-177">Company name</span></span>|
   ||<span data-ttu-id="833c6-178">BackColor</span><span class="sxs-lookup"><span data-stu-id="833c6-178">Backcolor</span></span>|<span data-ttu-id="833c6-179">Niebieski</span><span class="sxs-lookup"><span data-stu-id="833c6-179">Blue</span></span>|
   ||<span data-ttu-id="833c6-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="833c6-180">Forecolor</span></span>|<span data-ttu-id="833c6-181">Żółty</span><span class="sxs-lookup"><span data-stu-id="833c6-181">Yellow</span></span>|
   ||<span data-ttu-id="833c6-182">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="833c6-182">Font size</span></span>|<span data-ttu-id="833c6-183">18</span><span class="sxs-lookup"><span data-stu-id="833c6-183">18</span></span>|
   |<span data-ttu-id="833c6-184">Etykieta</span><span class="sxs-lookup"><span data-stu-id="833c6-184">Label</span></span>|<span data-ttu-id="833c6-185">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-185">Name</span></span>|<span data-ttu-id="833c6-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="833c6-186">customerLabel</span></span>|
   ||<span data-ttu-id="833c6-187">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-187">Text</span></span>|<span data-ttu-id="833c6-188">Nazwa &</span><span class="sxs-lookup"><span data-stu-id="833c6-188">&Name</span></span>|
   ||<span data-ttu-id="833c6-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-189">TabIndex</span></span>|<span data-ttu-id="833c6-190">2</span><span class="sxs-lookup"><span data-stu-id="833c6-190">2</span></span>|
   ||<span data-ttu-id="833c6-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-191">AccessibleDescription</span></span>|<span data-ttu-id="833c6-192">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="833c6-192">Customer name label</span></span>|
   ||<span data-ttu-id="833c6-193">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-193">AccessibleName</span></span>|<span data-ttu-id="833c6-194">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="833c6-194">Customer name label</span></span>|
   ||<span data-ttu-id="833c6-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="833c6-195">UseMnemonic</span></span>|<span data-ttu-id="833c6-196">True</span><span class="sxs-lookup"><span data-stu-id="833c6-196">True</span></span>|
   |<span data-ttu-id="833c6-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="833c6-197">TextBox</span></span>|<span data-ttu-id="833c6-198">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-198">Name</span></span>|<span data-ttu-id="833c6-199">customerName</span><span class="sxs-lookup"><span data-stu-id="833c6-199">customerName</span></span>|
   ||<span data-ttu-id="833c6-200">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-200">Text</span></span>|<span data-ttu-id="833c6-201">dawaj</span><span class="sxs-lookup"><span data-stu-id="833c6-201">(none)</span></span>|
   ||<span data-ttu-id="833c6-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-202">TabIndex</span></span>|<span data-ttu-id="833c6-203">3</span><span class="sxs-lookup"><span data-stu-id="833c6-203">3</span></span>|
   ||<span data-ttu-id="833c6-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-204">AccessibleDescription</span></span>|<span data-ttu-id="833c6-205">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="833c6-205">Customer name</span></span>|
   ||<span data-ttu-id="833c6-206">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-206">AccessibleName</span></span>|<span data-ttu-id="833c6-207">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="833c6-207">Customer name</span></span>|
   |<span data-ttu-id="833c6-208">Używane</span><span class="sxs-lookup"><span data-stu-id="833c6-208">GroupBox</span></span>|<span data-ttu-id="833c6-209">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-209">Name</span></span>|<span data-ttu-id="833c6-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="833c6-210">sizeOptions</span></span>|
   ||<span data-ttu-id="833c6-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-211">AccessibleDescription</span></span>|<span data-ttu-id="833c6-212">Opcje rozmiaru Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-212">Pizza size options</span></span>|
   ||<span data-ttu-id="833c6-213">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-213">AccessibleName</span></span>|<span data-ttu-id="833c6-214">Opcje rozmiaru Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-214">Pizza size options</span></span>|
   ||<span data-ttu-id="833c6-215">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-215">Text</span></span>|<span data-ttu-id="833c6-216">Rozmiar Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-216">Pizza size</span></span>|
   ||<span data-ttu-id="833c6-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-217">TabIndex</span></span>|<span data-ttu-id="833c6-218">4</span><span class="sxs-lookup"><span data-stu-id="833c6-218">4</span></span>|
   |<span data-ttu-id="833c6-219">Składniki</span><span class="sxs-lookup"><span data-stu-id="833c6-219">RadioButton</span></span>|<span data-ttu-id="833c6-220">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-220">Name</span></span>|<span data-ttu-id="833c6-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="833c6-221">smallPizza</span></span>|
   ||<span data-ttu-id="833c6-222">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-222">Text</span></span>|<span data-ttu-id="833c6-223">& mała $6,00</span><span class="sxs-lookup"><span data-stu-id="833c6-223">&Small $6.00</span></span>|
   ||<span data-ttu-id="833c6-224">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="833c6-224">Checked</span></span>|<span data-ttu-id="833c6-225">True</span><span class="sxs-lookup"><span data-stu-id="833c6-225">True</span></span>|
   ||<span data-ttu-id="833c6-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-226">TabIndex</span></span>|<span data-ttu-id="833c6-227">0</span><span class="sxs-lookup"><span data-stu-id="833c6-227">0</span></span>|
   ||<span data-ttu-id="833c6-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-228">AccessibleDescription</span></span>|<span data-ttu-id="833c6-229">Mały Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-229">Small pizza</span></span>|
   ||<span data-ttu-id="833c6-230">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-230">AccessibleName</span></span>|<span data-ttu-id="833c6-231">Mały Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-231">Small pizza</span></span>|
   |<span data-ttu-id="833c6-232">Składniki</span><span class="sxs-lookup"><span data-stu-id="833c6-232">RadioButton</span></span>|<span data-ttu-id="833c6-233">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-233">Name</span></span>|<span data-ttu-id="833c6-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="833c6-234">largePizza</span></span>|
   ||<span data-ttu-id="833c6-235">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-235">Text</span></span>|<span data-ttu-id="833c6-236">& duże $10,00</span><span class="sxs-lookup"><span data-stu-id="833c6-236">&Large $10.00</span></span>|
   ||<span data-ttu-id="833c6-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-237">TabIndex</span></span>|<span data-ttu-id="833c6-238">1</span><span class="sxs-lookup"><span data-stu-id="833c6-238">1</span></span>|
   ||<span data-ttu-id="833c6-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-239">AccessibleDescription</span></span>|<span data-ttu-id="833c6-240">Duże Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-240">Large pizza</span></span>|
   ||<span data-ttu-id="833c6-241">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-241">AccessibleName</span></span>|<span data-ttu-id="833c6-242">Duże Pizza</span><span class="sxs-lookup"><span data-stu-id="833c6-242">Large pizza</span></span>|
   |<span data-ttu-id="833c6-243">Etykieta</span><span class="sxs-lookup"><span data-stu-id="833c6-243">Label</span></span>|<span data-ttu-id="833c6-244">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-244">Name</span></span>|<span data-ttu-id="833c6-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="833c6-245">toppingsLabel</span></span>|
   ||<span data-ttu-id="833c6-246">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-246">Text</span></span>|<span data-ttu-id="833c6-247">& toppings ($0,75)</span><span class="sxs-lookup"><span data-stu-id="833c6-247">&Toppings ($0.75 each)</span></span>|
   ||<span data-ttu-id="833c6-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-248">TabIndex</span></span>|<span data-ttu-id="833c6-249">5</span><span class="sxs-lookup"><span data-stu-id="833c6-249">5</span></span>|
   ||<span data-ttu-id="833c6-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-250">AccessibleDescription</span></span>|<span data-ttu-id="833c6-251">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="833c6-251">Toppings label</span></span>|
   ||<span data-ttu-id="833c6-252">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-252">AccessibleName</span></span>|<span data-ttu-id="833c6-253">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="833c6-253">Toppings label</span></span>|
   ||<span data-ttu-id="833c6-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="833c6-254">UseMnemonic</span></span>|<span data-ttu-id="833c6-255">True</span><span class="sxs-lookup"><span data-stu-id="833c6-255">True</span></span>|
   |<span data-ttu-id="833c6-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="833c6-256">CheckedListBox</span></span>|<span data-ttu-id="833c6-257">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-257">Name</span></span>|<span data-ttu-id="833c6-258">toppings</span><span class="sxs-lookup"><span data-stu-id="833c6-258">toppings</span></span>|
   ||<span data-ttu-id="833c6-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-259">TabIndex</span></span>|<span data-ttu-id="833c6-260">6</span><span class="sxs-lookup"><span data-stu-id="833c6-260">6</span></span>|
   ||<span data-ttu-id="833c6-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-261">AccessibleDescription</span></span>|<span data-ttu-id="833c6-262">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="833c6-262">Available toppings</span></span>|
   ||<span data-ttu-id="833c6-263">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-263">AccessibleName</span></span>|<span data-ttu-id="833c6-264">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="833c6-264">Available toppings</span></span>|
   ||<span data-ttu-id="833c6-265">Items</span><span class="sxs-lookup"><span data-stu-id="833c6-265">Items</span></span>|<span data-ttu-id="833c6-266">Pepperoni, kiełbasy, grzyby</span><span class="sxs-lookup"><span data-stu-id="833c6-266">Pepperoni, Sausage, Mushrooms</span></span>|
   |<span data-ttu-id="833c6-267">Button</span><span class="sxs-lookup"><span data-stu-id="833c6-267">Button</span></span>|<span data-ttu-id="833c6-268">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-268">Name</span></span>|<span data-ttu-id="833c6-269">Porządek</span><span class="sxs-lookup"><span data-stu-id="833c6-269">order</span></span>|
   ||<span data-ttu-id="833c6-270">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-270">Text</span></span>|<span data-ttu-id="833c6-271">Kolejność &</span><span class="sxs-lookup"><span data-stu-id="833c6-271">&Order</span></span>|
   ||<span data-ttu-id="833c6-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-272">TabIndex</span></span>|<span data-ttu-id="833c6-273">7</span><span class="sxs-lookup"><span data-stu-id="833c6-273">7</span></span>|
   ||<span data-ttu-id="833c6-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-274">AccessibleDescription</span></span>|<span data-ttu-id="833c6-275">Suma zamówienia</span><span class="sxs-lookup"><span data-stu-id="833c6-275">Total the order</span></span>|
   ||<span data-ttu-id="833c6-276">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-276">AccessibleName</span></span>|<span data-ttu-id="833c6-277">Suma zamówień</span><span class="sxs-lookup"><span data-stu-id="833c6-277">Total order</span></span>|
   |<span data-ttu-id="833c6-278">Button</span><span class="sxs-lookup"><span data-stu-id="833c6-278">Button</span></span>|<span data-ttu-id="833c6-279">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-279">Name</span></span>|<span data-ttu-id="833c6-280">Anuluj</span><span class="sxs-lookup"><span data-stu-id="833c6-280">cancel</span></span>|
   ||<span data-ttu-id="833c6-281">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-281">Text</span></span>|<span data-ttu-id="833c6-282">& Anuluj</span><span class="sxs-lookup"><span data-stu-id="833c6-282">&Cancel</span></span>|
   ||<span data-ttu-id="833c6-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="833c6-283">TabIndex</span></span>|<span data-ttu-id="833c6-284">8</span><span class="sxs-lookup"><span data-stu-id="833c6-284">8</span></span>|
   ||<span data-ttu-id="833c6-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="833c6-285">AccessibleDescription</span></span>|<span data-ttu-id="833c6-286">Anulowanie zamówienia</span><span class="sxs-lookup"><span data-stu-id="833c6-286">Cancel the order</span></span>|
   ||<span data-ttu-id="833c6-287">Dostępname</span><span class="sxs-lookup"><span data-stu-id="833c6-287">AccessibleName</span></span>|<span data-ttu-id="833c6-288">Anulowanie zamówienia</span><span class="sxs-lookup"><span data-stu-id="833c6-288">Cancel order</span></span>|
   |<span data-ttu-id="833c6-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="833c6-289">MainMenu</span></span>|<span data-ttu-id="833c6-290">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-290">Name</span></span>|<span data-ttu-id="833c6-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="833c6-291">theMainMenu</span></span>|
   |<span data-ttu-id="833c6-292">Elementem</span><span class="sxs-lookup"><span data-stu-id="833c6-292">MenuItem</span></span>|<span data-ttu-id="833c6-293">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-293">Name</span></span>|<span data-ttu-id="833c6-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="833c6-294">fileCommands</span></span>|
   ||<span data-ttu-id="833c6-295">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-295">Text</span></span>|<span data-ttu-id="833c6-296">Plik &</span><span class="sxs-lookup"><span data-stu-id="833c6-296">&File</span></span>|
   |<span data-ttu-id="833c6-297">Elementem</span><span class="sxs-lookup"><span data-stu-id="833c6-297">MenuItem</span></span>|<span data-ttu-id="833c6-298">Nazwa</span><span class="sxs-lookup"><span data-stu-id="833c6-298">Name</span></span>|<span data-ttu-id="833c6-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="833c6-299">exitApp</span></span>|
   ||<span data-ttu-id="833c6-300">Tekst</span><span class="sxs-lookup"><span data-stu-id="833c6-300">Text</span></span>|<span data-ttu-id="833c6-301">E & kończ</span><span class="sxs-lookup"><span data-stu-id="833c6-301">E&xit</span></span>|

   <span data-ttu-id="833c6-302">Formularz będzie wyglądać podobnie jak na poniższym obrazie:</span><span class="sxs-lookup"><span data-stu-id="833c6-302">Your form will look something like the following image:</span></span>

   ![Formularz zamówienia Pizza z nazwą pola tekstowego oraz rozmiarem i toppings zaznaczeniem.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="833c6-304">Tryb obsługi duży kontrast</span><span class="sxs-lookup"><span data-stu-id="833c6-304">Supporting High Contrast Mode</span></span>

<span data-ttu-id="833c6-305">Tryb duży kontrast to ustawienie systemu Windows, które zwiększa czytelność przy użyciu kolorów kontrastu i rozmiarów czcionek, które są korzystne dla użytkowników niedowidzących.</span><span class="sxs-lookup"><span data-stu-id="833c6-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="833c6-306">Właściwość <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> jest dostarczana, aby określić, czy tryb duży kontrast jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="833c6-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>

<span data-ttu-id="833c6-307">Jeśli SystemInformation. HighContrast jest `true`, aplikacja powinna:</span><span class="sxs-lookup"><span data-stu-id="833c6-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>

- <span data-ttu-id="833c6-308">Wyświetlanie wszystkich elementów interfejsu użytkownika przy użyciu schematu kolorów systemu</span><span class="sxs-lookup"><span data-stu-id="833c6-308">Display all user interface elements using the system color scheme</span></span>

- <span data-ttu-id="833c6-309">Przekazuj podpowiedzi wizualne lub dźwiękowe informacje, które są przekazywane przez kolor.</span><span class="sxs-lookup"><span data-stu-id="833c6-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="833c6-310">Na przykład, jeśli konkretne elementy listy są wyróżnione przy użyciu czerwonej czcionki, można również dodać pogrubienie do czcionki, aby użytkownik miał niekolorową sygnalizację, że elementy są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="833c6-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>

- <span data-ttu-id="833c6-311">Pomiń wszystkie obrazy lub wzorce w tle tekstu</span><span class="sxs-lookup"><span data-stu-id="833c6-311">Omit any images or patterns behind text</span></span>

<span data-ttu-id="833c6-312">Aplikacja powinna sprawdzić ustawienie <xref:System.Windows.Forms.SystemInformation.HighContrast%2A>, gdy aplikacja zostanie uruchomiona i odpowie na zdarzenie systemowe <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="833c6-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="833c6-313">Zdarzenie <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> jest zgłaszane przy każdej zmianie wartości <xref:System.Windows.Forms.SystemInformation.HighContrast%2A>.</span><span class="sxs-lookup"><span data-stu-id="833c6-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>

<span data-ttu-id="833c6-314">W naszej aplikacji jedynym elementem, który nie korzysta z ustawień systemowych dla koloru jest `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="833c6-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="833c6-315">Klasa <xref:System.Drawing.SystemColors> służy do zmiany ustawień koloru etykiety na kolory systemu wybrane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="833c6-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="833c6-316">Aby włączyć tryb duży kontrast w skuteczny sposób</span><span class="sxs-lookup"><span data-stu-id="833c6-316">To enable High Contrast mode in an effective way</span></span>

1. <span data-ttu-id="833c6-317">Utwórz metodę, aby ustawić kolory etykiety na kolory systemowe.</span><span class="sxs-lookup"><span data-stu-id="833c6-317">Create a method to set the colors of the label to the system colors.</span></span>

    ```vb
    Private Sub SetColorScheme()
        If SystemInformation.HighContrast Then
            companyLabel.BackColor = SystemColors.Window
            companyLabel.ForeColor = SystemColors.WindowText
        Else
            companyLabel.BackColor = Color.Blue
            companyLabel.ForeColor = Color.Yellow
        End If
    End Sub
    ```

    ```csharp
    private void SetColorScheme()
    {
        if (SystemInformation.HighContrast)
        {
            companyLabel.BackColor = SystemColors.Window;
            companyLabel.ForeColor = SystemColors.WindowText;
        }
        else
        {
            companyLabel.BackColor = Color.Blue;
            companyLabel.ForeColor = Color.Yellow;
        }
    }
    ```

2. <span data-ttu-id="833c6-318">Wywołaj procedurę `SetColorScheme` w konstruktorze formularzy (`Public Sub New()` w Visual Basic i `public Form1()` w wizualizacji C#).</span><span class="sxs-lookup"><span data-stu-id="833c6-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public Form1()` in Visual C#).</span></span> <span data-ttu-id="833c6-319">Aby uzyskać dostęp do konstruktora w Visual Basic, należy rozwinąć region o nazwie **kod wygenerowany przez projektanta formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="833c6-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
    }
    ```

3. <span data-ttu-id="833c6-320">Utwórz procedurę zdarzenia z odpowiednim podpisem, aby odpowiedzieć na zdarzenie <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="833c6-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>

    ```vb
    Protected Sub UserPreferenceChanged(sender As Object, _
    e As Microsoft.Win32.UserPreferenceChangedEventArgs)
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
        SetColorScheme();
    }
    ```

4. <span data-ttu-id="833c6-321">Dodaj kod do konstruktora formularzy po wywołaniu do `InitializeComponents`, aby podłączyć procedurę zdarzenia do zdarzenia systemowego.</span><span class="sxs-lookup"><span data-stu-id="833c6-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="833c6-322">Ta metoda wywołuje procedurę `SetColorScheme`.</span><span class="sxs-lookup"><span data-stu-id="833c6-322">This method calls the `SetColorScheme` procedure.</span></span>

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
        AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           += new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
    }
    ```

5. <span data-ttu-id="833c6-323">Dodaj kod do metody <xref:System.Windows.Forms.Control.Dispose%2A> przed wywołaniem metody <xref:System.Windows.Forms.Control.Dispose%2A> klasy bazowej, aby zwolnić zdarzenie po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="833c6-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="833c6-324">Aby uzyskać dostęp do metody <xref:System.Windows.Forms.Control.Dispose%2A> w Visual Basic, należy rozwinąć region o nazwie kod wygenerowany przez projektanta formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="833c6-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="833c6-325">Kod zdarzenia systemowego uruchamia wątek oddzielony od głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="833c6-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="833c6-326">Jeśli nie zwolnisz zdarzenia, kod, który zostanie poddany do zdarzenia, zostanie uruchomiony nawet po zamknięciu programu.</span><span class="sxs-lookup"><span data-stu-id="833c6-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>

    ```vb
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)
        If disposing AndAlso components IsNot Nothing Then
            components.Dispose()
        End If
        RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
        MyBase.Dispose(disposing)
    End Sub
    ```

    ```csharp
    protected override void Dispose(bool disposing)
    {
        if(disposing && components != null)
        {
            components.Dispose();
        }
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           -= new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
        base.Dispose( disposing );
    }
    ```

6. <span data-ttu-id="833c6-327">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="833c6-327">Press F5 to run the application.</span></span>

## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="833c6-328">Przekazywanie ważnych informacji przy użyciu metody innej niż dźwięk</span><span class="sxs-lookup"><span data-stu-id="833c6-328">Conveying Important Information by Means Other Than Sound</span></span>

<span data-ttu-id="833c6-329">W tej aplikacji żadne informacje nie są przekazywane przez sam dźwięk.</span><span class="sxs-lookup"><span data-stu-id="833c6-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="833c6-330">Jeśli używasz dźwięku w aplikacji, należy również podać informacje o innych sposobach.</span><span class="sxs-lookup"><span data-stu-id="833c6-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>

#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="833c6-331">Aby podać informacje w inny sposób niż dźwięk</span><span class="sxs-lookup"><span data-stu-id="833c6-331">To supply information by some other means than sound</span></span>

1. <span data-ttu-id="833c6-332">Zmień pasek tytułu na Flash przy użyciu funkcji interfejsu API systemu Windows FlashWindow.</span><span class="sxs-lookup"><span data-stu-id="833c6-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="833c6-333">Przykład sposobu wywoływania funkcji interfejsu API systemu Windows można znaleźć w [przewodniku: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="833c6-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="833c6-334">Użytkownik może mieć włączoną usługę Windows WartownikDźwięków, co spowoduje również, że okno zostanie wybłyskowe, gdy dźwięki systemu są odtwarzane za pomocą wbudowanego głośnika komputera.</span><span class="sxs-lookup"><span data-stu-id="833c6-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>

2. <span data-ttu-id="833c6-335">Wyświetl ważne informacje w oknie niemodalnym, aby użytkownik mógł je odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="833c6-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>

3. <span data-ttu-id="833c6-336">Wyświetla okno komunikatu, które uzyskuje fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="833c6-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="833c6-337">Należy unikać tej metody, gdy użytkownik może pisać.</span><span class="sxs-lookup"><span data-stu-id="833c6-337">Avoid this method when the user may be typing.</span></span>

4. <span data-ttu-id="833c6-338">Wyświetl wskaźnik stanu w obszarze powiadomień o stanie na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="833c6-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="833c6-339">Aby uzyskać szczegółowe informacje, zobacz [Dodawanie ikon aplikacji do paska zadań ze składnikiem Windows Forms NotifyIcon](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="833c6-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>

## <a name="testing-the-application"></a><span data-ttu-id="833c6-340">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="833c6-340">Testing the Application</span></span>

<span data-ttu-id="833c6-341">Przed wdrożeniem aplikacji należy przetestować funkcje ułatwień dostępu, które zostały zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="833c6-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>

#### <a name="to-test-accessibility-features"></a><span data-ttu-id="833c6-342">Aby przetestować funkcje ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="833c6-342">To test accessibility features</span></span>

1. <span data-ttu-id="833c6-343">Aby przetestować dostęp do klawiatury, odłącz mysz i przejdź do interfejsu użytkownika dla każdej funkcji przy użyciu tylko klawiatury.</span><span class="sxs-lookup"><span data-stu-id="833c6-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="833c6-344">Upewnij się, że wszystkie zadania mogą być wykonywane tylko przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="833c6-344">Ensure that all tasks may be performed using the keyboard only.</span></span>

2. <span data-ttu-id="833c6-345">Aby przetestować obsługę duży kontrast, wybierz ikonę Opcje ułatwień dostępu w panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="833c6-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="833c6-346">Kliknij kartę Wyświetlanie, a następnie zaznacz pole wyboru Użyj duży kontrast.</span><span class="sxs-lookup"><span data-stu-id="833c6-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="833c6-347">Przejdź przez wszystkie elementy interfejsu użytkownika, aby upewnić się, że zmiany koloru i czcionki są odzwierciedlone.</span><span class="sxs-lookup"><span data-stu-id="833c6-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="833c6-348">Upewnij się również, że obrazy lub wzorce rysowane w tle tekstu są pomijane.</span><span class="sxs-lookup"><span data-stu-id="833c6-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>

    > [!NOTE]
    > <span data-ttu-id="833c6-349">W systemie Windows NT 4 nie ma ikony Opcje ułatwień dostępu w panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="833c6-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="833c6-350">W rezultacie ta procedura zmiany ustawienia SystemInformation. HighContrast nie działa w systemie Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="833c6-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>

3. <span data-ttu-id="833c6-351">Inne narzędzia są łatwo dostępne do testowania dostępności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="833c6-351">Other tools are readily available for testing the accessibility of an application.</span></span>

4. <span data-ttu-id="833c6-352">Aby przetestować Uwidacznianie fokusu klawiatury, uruchom program Lupa.</span><span class="sxs-lookup"><span data-stu-id="833c6-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="833c6-353">(Aby otworzyć, kliknij menu **Start** , wskaż pozycję **programy**, wskaż pozycję **akcesoria**, wskaż pozycję **ułatwienia dostępu**, a następnie kliknij pozycję **Lupa**).</span><span class="sxs-lookup"><span data-stu-id="833c6-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="833c6-354">Przejdź do interfejsu użytkownika, używając klawisza Tab i myszy.</span><span class="sxs-lookup"><span data-stu-id="833c6-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="833c6-355">Upewnij się, że cała nawigacja jest prawidłowo śledzona w programie **Lupa**.</span><span class="sxs-lookup"><span data-stu-id="833c6-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>

5. <span data-ttu-id="833c6-356">Aby przetestować Uwidacznianie elementów ekranu, uruchom inspekcję i użyj zarówno myszy, jak i klawisza TAB, aby dotrzeć do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="833c6-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="833c6-357">Upewnij się, że informacje prezentowane w polach Nazwa, stan, rola, lokalizacja i wartość okna inspekcji są zrozumiałe dla użytkownika dla każdego obiektu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="833c6-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
