---
title: 'Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: c324e4956d6db29e4de12bd7639a69daaf65d872
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665927"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="b082a-102">Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows</span><span class="sxs-lookup"><span data-stu-id="b082a-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="b082a-103">Tworzenie dostępnej aplikacji ma skutki dla firmy ważne.</span><span class="sxs-lookup"><span data-stu-id="b082a-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="b082a-104">Wiele rządy mieć ułatwień dostępu przepisami lub ustaleniami dotyczącymi oprogramowania zakupionego.</span><span class="sxs-lookup"><span data-stu-id="b082a-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="b082a-105">Logo Certified for Windows zawiera wymagania dotyczące ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="b082a-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="b082a-106">Szacowany mieszkańcy 30 mln Stanów Zjednoczonych samodzielnie, wiele potencjalnych klientów, są zagrożone dostępność oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="b082a-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="b082a-107">Ten przewodnik pozwala sprostać pięć wymagania dotyczące ułatwień dostępu, logo Certified for Windows.</span><span class="sxs-lookup"><span data-stu-id="b082a-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="b082a-108">Zgodnie z tymi wymaganiami dostępnej aplikacji wykonują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b082a-108">According to these requirements, an accessible application will:</span></span>  
  
- <span data-ttu-id="b082a-109">Obsługuje rozmiar panelu sterowania, kolory, czcionki i wprowadź ustawienia.</span><span class="sxs-lookup"><span data-stu-id="b082a-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="b082a-110">Pasek menu, pasek tytułu, obramowania i pasek stanu będzie wszystkie rozmiar się po użytkownik zmienia ustawienia Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="b082a-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="b082a-111">Nie dodatkowe zmiany do kontrolki lub kodu są wymagane w tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b082a-111">No additional changes to the controls or code are required in this application.</span></span>  
  
- <span data-ttu-id="b082a-112">Obsługa trybu wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="b082a-112">Support High Contrast mode.</span></span>  
  
- <span data-ttu-id="b082a-113">Podaj udokumentowanego klawiatury dostęp do wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="b082a-113">Provide documented keyboard access to all features.</span></span>  
  
- <span data-ttu-id="b082a-114">Udostępnianie lokalizacji fokus klawiatury ModelID.</span><span class="sxs-lookup"><span data-stu-id="b082a-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
- <span data-ttu-id="b082a-115">Należy unikać przekazywania ważnych informacji za pomocą dźwięku samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b082a-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="b082a-116">Aby uzyskać więcej informacji, zobacz [zasoby do projektowania dostępnych aplikacji](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="b082a-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="b082a-117">Aby uzyskać informacje dotyczące obsługi różnych układów klawiatury, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="b082a-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b082a-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="b082a-118">Creating the Project</span></span>  
 <span data-ttu-id="b082a-119">Ten poradnik tworzy interfejsu użytkownika dla aplikacji, która przyjmuje pizza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="b082a-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="b082a-120">Składa się z <xref:System.Windows.Forms.TextBox> dla nazwy klienta <xref:System.Windows.Forms.RadioButton> grupy, aby wybrać rozmiar pizza <xref:System.Windows.Forms.CheckedListBox> służąca do wybierania toppings, dwie kontrolki przycisku etykietą, kolejność i Anuluj i Menu przy użyciu polecenia Exit.</span><span class="sxs-lookup"><span data-stu-id="b082a-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="b082a-121">Użytkownik wprowadza nazwę klienta, rozmiar pizza i toppings żądanego.</span><span class="sxs-lookup"><span data-stu-id="b082a-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="b082a-122">Gdy użytkownik kliknie przycisk Zamówienie, podsumowanie kolejności i jego kosztów są wyświetlane w oknie komunikatu i formanty są wyczyszczone i jest gotowa do następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b082a-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="b082a-123">Gdy użytkownik kliknie przycisk Anuluj, formanty są wyczyszczone i jest gotowa do następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b082a-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="b082a-124">Gdy użytkownik kliknie element menu zakończenia, zamyka program.</span><span class="sxs-lookup"><span data-stu-id="b082a-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="b082a-125">Szczególnym w tym przewodniku nie jest w kodzie system zamówień sprzedaży detalicznej, ale dostępność interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b082a-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="b082a-126">Instruktaż demonstruje funkcje ułatwień dostępu kilka często używanych formantów, w tym przycisków, przyciski radiowe, pola tekstowe i etykiety.</span><span class="sxs-lookup"><span data-stu-id="b082a-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="b082a-127">Aby rozpocząć tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b082a-127">To begin making the application</span></span>  
  
- <span data-ttu-id="b082a-128">Utwórz nową aplikację Windows w języku Visual Basic lub Visual C#.</span><span class="sxs-lookup"><span data-stu-id="b082a-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="b082a-129">Nadaj projektowi nazwę **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="b082a-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="b082a-130">(Aby uzyskać szczegółowe informacje, zobacz [tworzenie nowych rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="b082a-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="b082a-131">Dodawanie formantów do formularza</span><span class="sxs-lookup"><span data-stu-id="b082a-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="b082a-132">Podczas dodawania formantów do formularza, należy pamiętać, poniższe wskazówki umożliwiają dostępnej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b082a-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
- <span data-ttu-id="b082a-133">Ustaw <xref:System.Windows.Forms.Control.AccessibleDescription%2A> i <xref:System.Windows.Forms.Control.AccessibleName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b082a-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="b082a-134">W tym przykładzie domyślne ustawienie dla <xref:System.Windows.Forms.Control.AccessibleRole%2A> jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="b082a-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="b082a-135">Aby uzyskać więcej informacji na temat właściwości ułatwień dostępu, zobacz [dostarczanie informacji o ułatwieniach dostępu dla formantów w formularzu Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="b082a-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
- <span data-ttu-id="b082a-136">Ustaw rozmiar czcionki do 10 punktów i większych.</span><span class="sxs-lookup"><span data-stu-id="b082a-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b082a-137">Jeśli ustawisz rozmiar czcionki w formularzu do 10 podczas uruchamiania, wszystkie kontrolki, następnie dodawane do formularza będzie miał rozmiar czcionki, 10.</span><span class="sxs-lookup"><span data-stu-id="b082a-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
- <span data-ttu-id="b082a-138">Upewnij się, że wszystkie kontrolki etykiety, która opisuje kontrolki TextBox bezpośrednio poprzedza formant pola tekstowego w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="b082a-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
- <span data-ttu-id="b082a-139">Dodaj klucz dostępu, korzystając ze znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> dowolną kontrolkę, użytkownik może chcieć przejść do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b082a-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
- <span data-ttu-id="b082a-140">Dodaj klucz dostępu, korzystając ze znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> właściwość etykiety, który poprzedza formant, który użytkownik może chcieć przejść do.</span><span class="sxs-lookup"><span data-stu-id="b082a-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="b082a-141">Ustawić etykiety <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true`, dzięki czemu fokus jest ustawiony do następnej kontrolki w kolejności tabulacji, gdy użytkownik naciśnie klawisz dostępu.</span><span class="sxs-lookup"><span data-stu-id="b082a-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
- <span data-ttu-id="b082a-142">Dodaj klucze dostępu do wszystkich elementów menu.</span><span class="sxs-lookup"><span data-stu-id="b082a-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="b082a-143">Aby udostępnić aplikację Windows</span><span class="sxs-lookup"><span data-stu-id="b082a-143">To make your Windows Application accessible</span></span>  
  
- <span data-ttu-id="b082a-144">Dodaj formanty do formularza, a następnie ustaw właściwości, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="b082a-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="b082a-145">Zobacz obraz na koniec tabeli dla modeli rozmieszczanie formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b082a-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="b082a-146">Obiekt</span><span class="sxs-lookup"><span data-stu-id="b082a-146">Object</span></span>|<span data-ttu-id="b082a-147">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b082a-147">Property</span></span>|<span data-ttu-id="b082a-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="b082a-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="b082a-149">Formularz Form1</span><span class="sxs-lookup"><span data-stu-id="b082a-149">Form1</span></span>|<span data-ttu-id="b082a-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-150">AccessibleDescription</span></span>|<span data-ttu-id="b082a-151">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="b082a-151">Order form</span></span>|  
    ||<span data-ttu-id="b082a-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-152">AccessibleName</span></span>|<span data-ttu-id="b082a-153">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="b082a-153">Order form</span></span>|  
    ||<span data-ttu-id="b082a-154">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="b082a-154">Font Size</span></span>|<span data-ttu-id="b082a-155">10</span><span class="sxs-lookup"><span data-stu-id="b082a-155">10</span></span>|  
    ||<span data-ttu-id="b082a-156">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-156">Text</span></span>|<span data-ttu-id="b082a-157">Formularz zamówienia pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="b082a-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="b082a-158">PictureBox</span></span>|<span data-ttu-id="b082a-159">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-159">Name</span></span>|<span data-ttu-id="b082a-160">logo</span><span class="sxs-lookup"><span data-stu-id="b082a-160">logo</span></span>|  
    ||<span data-ttu-id="b082a-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-161">AccessibleDescription</span></span>|<span data-ttu-id="b082a-162">Wycinek pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="b082a-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-163">AccessibleName</span></span>|<span data-ttu-id="b082a-164">Logo firmy</span><span class="sxs-lookup"><span data-stu-id="b082a-164">Company logo</span></span>|  
    ||<span data-ttu-id="b082a-165">Obraz</span><span class="sxs-lookup"><span data-stu-id="b082a-165">Image</span></span>|<span data-ttu-id="b082a-166">Wszystkie ikony lub mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="b082a-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="b082a-167">Etykieta</span><span class="sxs-lookup"><span data-stu-id="b082a-167">Label</span></span>|<span data-ttu-id="b082a-168">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-168">Name</span></span>|<span data-ttu-id="b082a-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="b082a-169">companyLabel</span></span>|  
    ||<span data-ttu-id="b082a-170">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-170">Text</span></span>|<span data-ttu-id="b082a-171">Dobre Pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="b082a-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-172">TabIndex</span></span>|<span data-ttu-id="b082a-173">1</span><span class="sxs-lookup"><span data-stu-id="b082a-173">1</span></span>|  
    ||<span data-ttu-id="b082a-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-174">AccessibleDescription</span></span>|<span data-ttu-id="b082a-175">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="b082a-175">Company name</span></span>|  
    ||<span data-ttu-id="b082a-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-176">AccessibleName</span></span>|<span data-ttu-id="b082a-177">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="b082a-177">Company name</span></span>|  
    ||<span data-ttu-id="b082a-178">Backcolor</span><span class="sxs-lookup"><span data-stu-id="b082a-178">Backcolor</span></span>|<span data-ttu-id="b082a-179">Niebieski</span><span class="sxs-lookup"><span data-stu-id="b082a-179">Blue</span></span>|  
    ||<span data-ttu-id="b082a-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="b082a-180">Forecolor</span></span>|<span data-ttu-id="b082a-181">Żółty</span><span class="sxs-lookup"><span data-stu-id="b082a-181">Yellow</span></span>|  
    ||<span data-ttu-id="b082a-182">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="b082a-182">Font size</span></span>|<span data-ttu-id="b082a-183">18</span><span class="sxs-lookup"><span data-stu-id="b082a-183">18</span></span>|  
    |<span data-ttu-id="b082a-184">Etykieta</span><span class="sxs-lookup"><span data-stu-id="b082a-184">Label</span></span>|<span data-ttu-id="b082a-185">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-185">Name</span></span>|<span data-ttu-id="b082a-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="b082a-186">customerLabel</span></span>|  
    ||<span data-ttu-id="b082a-187">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-187">Text</span></span>|<span data-ttu-id="b082a-188">& Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-188">&Name</span></span>|  
    ||<span data-ttu-id="b082a-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-189">TabIndex</span></span>|<span data-ttu-id="b082a-190">2</span><span class="sxs-lookup"><span data-stu-id="b082a-190">2</span></span>|  
    ||<span data-ttu-id="b082a-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-191">AccessibleDescription</span></span>|<span data-ttu-id="b082a-192">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="b082a-192">Customer name label</span></span>|  
    ||<span data-ttu-id="b082a-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-193">AccessibleName</span></span>|<span data-ttu-id="b082a-194">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="b082a-194">Customer name label</span></span>|  
    ||<span data-ttu-id="b082a-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="b082a-195">UseMnemonic</span></span>|<span data-ttu-id="b082a-196">Prawda</span><span class="sxs-lookup"><span data-stu-id="b082a-196">True</span></span>|  
    |<span data-ttu-id="b082a-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="b082a-197">TextBox</span></span>|<span data-ttu-id="b082a-198">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-198">Name</span></span>|<span data-ttu-id="b082a-199">customerName</span><span class="sxs-lookup"><span data-stu-id="b082a-199">customerName</span></span>|  
    ||<span data-ttu-id="b082a-200">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-200">Text</span></span>|<span data-ttu-id="b082a-201">(Brak)</span><span class="sxs-lookup"><span data-stu-id="b082a-201">(none)</span></span>|  
    ||<span data-ttu-id="b082a-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-202">TabIndex</span></span>|<span data-ttu-id="b082a-203">3</span><span class="sxs-lookup"><span data-stu-id="b082a-203">3</span></span>|  
    ||<span data-ttu-id="b082a-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-204">AccessibleDescription</span></span>|<span data-ttu-id="b082a-205">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="b082a-205">Customer name</span></span>|  
    ||<span data-ttu-id="b082a-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-206">AccessibleName</span></span>|<span data-ttu-id="b082a-207">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="b082a-207">Customer name</span></span>|  
    |<span data-ttu-id="b082a-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="b082a-208">GroupBox</span></span>|<span data-ttu-id="b082a-209">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-209">Name</span></span>|<span data-ttu-id="b082a-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="b082a-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="b082a-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-211">AccessibleDescription</span></span>|<span data-ttu-id="b082a-212">Opcje rozmiaru pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="b082a-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-213">AccessibleName</span></span>|<span data-ttu-id="b082a-214">Opcje rozmiaru pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="b082a-215">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-215">Text</span></span>|<span data-ttu-id="b082a-216">Rozmiar pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-216">Pizza size</span></span>|  
    ||<span data-ttu-id="b082a-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-217">TabIndex</span></span>|<span data-ttu-id="b082a-218">4</span><span class="sxs-lookup"><span data-stu-id="b082a-218">4</span></span>|  
    |<span data-ttu-id="b082a-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="b082a-219">RadioButton</span></span>|<span data-ttu-id="b082a-220">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-220">Name</span></span>|<span data-ttu-id="b082a-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="b082a-221">smallPizza</span></span>|  
    ||<span data-ttu-id="b082a-222">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-222">Text</span></span>|<span data-ttu-id="b082a-223">& małe $6.00</span><span class="sxs-lookup"><span data-stu-id="b082a-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="b082a-224">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="b082a-224">Checked</span></span>|<span data-ttu-id="b082a-225">Prawda</span><span class="sxs-lookup"><span data-stu-id="b082a-225">True</span></span>|  
    ||<span data-ttu-id="b082a-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-226">TabIndex</span></span>|<span data-ttu-id="b082a-227">0</span><span class="sxs-lookup"><span data-stu-id="b082a-227">0</span></span>|  
    ||<span data-ttu-id="b082a-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-228">AccessibleDescription</span></span>|<span data-ttu-id="b082a-229">Małe pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-229">Small pizza</span></span>|  
    ||<span data-ttu-id="b082a-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-230">AccessibleName</span></span>|<span data-ttu-id="b082a-231">Małe pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-231">Small pizza</span></span>|  
    |<span data-ttu-id="b082a-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="b082a-232">RadioButton</span></span>|<span data-ttu-id="b082a-233">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-233">Name</span></span>|<span data-ttu-id="b082a-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="b082a-234">largePizza</span></span>|  
    ||<span data-ttu-id="b082a-235">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-235">Text</span></span>|<span data-ttu-id="b082a-236">& dużych 10,00 zł</span><span class="sxs-lookup"><span data-stu-id="b082a-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="b082a-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-237">TabIndex</span></span>|<span data-ttu-id="b082a-238">1</span><span class="sxs-lookup"><span data-stu-id="b082a-238">1</span></span>|  
    ||<span data-ttu-id="b082a-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-239">AccessibleDescription</span></span>|<span data-ttu-id="b082a-240">Duże pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-240">Large pizza</span></span>|  
    ||<span data-ttu-id="b082a-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-241">AccessibleName</span></span>|<span data-ttu-id="b082a-242">Duże pizza</span><span class="sxs-lookup"><span data-stu-id="b082a-242">Large pizza</span></span>|  
    |<span data-ttu-id="b082a-243">Etykieta</span><span class="sxs-lookup"><span data-stu-id="b082a-243">Label</span></span>|<span data-ttu-id="b082a-244">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-244">Name</span></span>|<span data-ttu-id="b082a-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="b082a-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="b082a-246">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-246">Text</span></span>|<span data-ttu-id="b082a-247">& toppings ($0,75 każdy)</span><span class="sxs-lookup"><span data-stu-id="b082a-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="b082a-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-248">TabIndex</span></span>|<span data-ttu-id="b082a-249">5</span><span class="sxs-lookup"><span data-stu-id="b082a-249">5</span></span>|  
    ||<span data-ttu-id="b082a-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-250">AccessibleDescription</span></span>|<span data-ttu-id="b082a-251">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="b082a-251">Toppings label</span></span>|  
    ||<span data-ttu-id="b082a-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-252">AccessibleName</span></span>|<span data-ttu-id="b082a-253">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="b082a-253">Toppings label</span></span>|  
    ||<span data-ttu-id="b082a-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="b082a-254">UseMnemonic</span></span>|<span data-ttu-id="b082a-255">Prawda</span><span class="sxs-lookup"><span data-stu-id="b082a-255">True</span></span>|  
    |<span data-ttu-id="b082a-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="b082a-256">CheckedListBox</span></span>|<span data-ttu-id="b082a-257">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-257">Name</span></span>|<span data-ttu-id="b082a-258">toppings</span><span class="sxs-lookup"><span data-stu-id="b082a-258">toppings</span></span>|  
    ||<span data-ttu-id="b082a-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-259">TabIndex</span></span>|<span data-ttu-id="b082a-260">6</span><span class="sxs-lookup"><span data-stu-id="b082a-260">6</span></span>|  
    ||<span data-ttu-id="b082a-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-261">AccessibleDescription</span></span>|<span data-ttu-id="b082a-262">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="b082a-262">Available toppings</span></span>|  
    ||<span data-ttu-id="b082a-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-263">AccessibleName</span></span>|<span data-ttu-id="b082a-264">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="b082a-264">Available toppings</span></span>|  
    ||<span data-ttu-id="b082a-265">Elementy</span><span class="sxs-lookup"><span data-stu-id="b082a-265">Items</span></span>|<span data-ttu-id="b082a-266">Pepperoni, produkcji kiełbas, grzyby</span><span class="sxs-lookup"><span data-stu-id="b082a-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="b082a-267">Przycisk</span><span class="sxs-lookup"><span data-stu-id="b082a-267">Button</span></span>|<span data-ttu-id="b082a-268">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-268">Name</span></span>|<span data-ttu-id="b082a-269">kolejność</span><span class="sxs-lookup"><span data-stu-id="b082a-269">order</span></span>|  
    ||<span data-ttu-id="b082a-270">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-270">Text</span></span>|<span data-ttu-id="b082a-271">& kolejność</span><span class="sxs-lookup"><span data-stu-id="b082a-271">&Order</span></span>|  
    ||<span data-ttu-id="b082a-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-272">TabIndex</span></span>|<span data-ttu-id="b082a-273">7</span><span class="sxs-lookup"><span data-stu-id="b082a-273">7</span></span>|  
    ||<span data-ttu-id="b082a-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-274">AccessibleDescription</span></span>|<span data-ttu-id="b082a-275">Łączna liczba kolejności</span><span class="sxs-lookup"><span data-stu-id="b082a-275">Total the order</span></span>|  
    ||<span data-ttu-id="b082a-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-276">AccessibleName</span></span>|<span data-ttu-id="b082a-277">Zamówienia</span><span class="sxs-lookup"><span data-stu-id="b082a-277">Total order</span></span>|  
    |<span data-ttu-id="b082a-278">Przycisk</span><span class="sxs-lookup"><span data-stu-id="b082a-278">Button</span></span>|<span data-ttu-id="b082a-279">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-279">Name</span></span>|<span data-ttu-id="b082a-280">Anuluj</span><span class="sxs-lookup"><span data-stu-id="b082a-280">cancel</span></span>|  
    ||<span data-ttu-id="b082a-281">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-281">Text</span></span>|<span data-ttu-id="b082a-282">& Anuluj</span><span class="sxs-lookup"><span data-stu-id="b082a-282">&Cancel</span></span>|  
    ||<span data-ttu-id="b082a-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="b082a-283">TabIndex</span></span>|<span data-ttu-id="b082a-284">8</span><span class="sxs-lookup"><span data-stu-id="b082a-284">8</span></span>|  
    ||<span data-ttu-id="b082a-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="b082a-285">AccessibleDescription</span></span>|<span data-ttu-id="b082a-286">Anulowanie zamówienia</span><span class="sxs-lookup"><span data-stu-id="b082a-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="b082a-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="b082a-287">AccessibleName</span></span>|<span data-ttu-id="b082a-288">Anulowanie zamówienia</span><span class="sxs-lookup"><span data-stu-id="b082a-288">Cancel order</span></span>|  
    |<span data-ttu-id="b082a-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="b082a-289">MainMenu</span></span>|<span data-ttu-id="b082a-290">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-290">Name</span></span>|<span data-ttu-id="b082a-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="b082a-291">theMainMenu</span></span>|  
    |<span data-ttu-id="b082a-292">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="b082a-292">MenuItem</span></span>|<span data-ttu-id="b082a-293">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-293">Name</span></span>|<span data-ttu-id="b082a-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="b082a-294">fileCommands</span></span>|  
    ||<span data-ttu-id="b082a-295">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-295">Text</span></span>|<span data-ttu-id="b082a-296">&File</span><span class="sxs-lookup"><span data-stu-id="b082a-296">&File</span></span>|  
    |<span data-ttu-id="b082a-297">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="b082a-297">MenuItem</span></span>|<span data-ttu-id="b082a-298">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b082a-298">Name</span></span>|<span data-ttu-id="b082a-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="b082a-299">exitApp</span></span>|  
    ||<span data-ttu-id="b082a-300">Tekst</span><span class="sxs-lookup"><span data-stu-id="b082a-300">Text</span></span>|<span data-ttu-id="b082a-301">Za & kończ</span><span class="sxs-lookup"><span data-stu-id="b082a-301">E&xit</span></span>|
    
      Your form will look something like the following image:
    
      ![The pizza order form with a name textbox, and size and toppings selection.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="b082a-302">Obsługa trybu wysokiego kontrastu</span><span class="sxs-lookup"><span data-stu-id="b082a-302">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="b082a-303">Trybu wysokiego kontrastu jest ustawienie systemu Windows, który poprawia czytelność przy użyciu kontrastujących i rozmiary czcionek, które są przydatne dla użytkowników niedowidzących.</span><span class="sxs-lookup"><span data-stu-id="b082a-303">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="b082a-304"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Właściwość została podana w celu ustalenia, czy ustawiono trybu wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="b082a-304">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="b082a-305">Jeśli jest SystemInformation.HighContrast `true`, aplikacja powinna:</span><span class="sxs-lookup"><span data-stu-id="b082a-305">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
- <span data-ttu-id="b082a-306">Wyświetlanie wszystkich elementów interfejsu użytkownika przy użyciu schematu kolorów systemu</span><span class="sxs-lookup"><span data-stu-id="b082a-306">Display all user interface elements using the system color scheme</span></span>  
  
- <span data-ttu-id="b082a-307">Przekazuje za pomocą wizualnych lub dźwięk wszystkie informacje, które jest przekazywane przez kolor.</span><span class="sxs-lookup"><span data-stu-id="b082a-307">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="b082a-308">Na przykład jeśli elementy konkretnej listy są wyróżnione za pomocą czerwonego czcionki, można również dodasz pogrubioną czcionką, tak, aby użytkownik miał cue-color, że elementy są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="b082a-308">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
- <span data-ttu-id="b082a-309">Pomiń wszelkie obrazy i wzorce pod tekstem</span><span class="sxs-lookup"><span data-stu-id="b082a-309">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="b082a-310">Aplikacja powinna sprawdzać, czy ustawienie <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> podczas uruchamiania aplikacji i odpowiedzieć na zdarzenie systemowe <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="b082a-310">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="b082a-311"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Zdarzenie jest wywoływane zawsze wtedy, gdy wartość <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> zmiany.</span><span class="sxs-lookup"><span data-stu-id="b082a-311">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="b082a-312">W naszej aplikacji jest jedynym elementem, który nie używa ustawień systemowych dla koloru `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="b082a-312">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="b082a-313"><xref:System.Drawing.SystemColors> Klasa jest używana, aby zmienić ustawienia koloru etykiety na kolory systemowe wybrane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b082a-313">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="b082a-314">Aby włączyć tryb dużego kontrastu w skutecznym sposobem</span><span class="sxs-lookup"><span data-stu-id="b082a-314">To enable High Contrast mode in an effective way</span></span>  
  
1. <span data-ttu-id="b082a-315">Utwórz metodę, aby ustawić kolory, etykiety kolory systemowe.</span><span class="sxs-lookup"><span data-stu-id="b082a-315">Create a method to set the colors of the label to the system colors.</span></span>  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
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
  
2. <span data-ttu-id="b082a-316">Wywołaj `SetColorScheme` procedury w Konstruktorze formularza (`Public Sub New()` w języku Visual Basic i `public class Form1` w elemencie wizualnym C#).</span><span class="sxs-lookup"><span data-stu-id="b082a-316">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="b082a-317">Aby uzyskać dostęp do konstruktora w języku Visual Basic, konieczne będzie rozwiń region etykietą **kod wygenerowany przez projektanta formularzy Windows**.</span><span class="sxs-lookup"><span data-stu-id="b082a-317">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3. <span data-ttu-id="b082a-318">Utwórz procedurę zdarzenia z odpowiednim podpisem, aby odpowiedzieć na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b082a-318">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4. <span data-ttu-id="b082a-319">Dodaj kod konstruktora formularza po wywołaniu `InitializeComponents`, żeby podpiąć procedury zdarzenia zdarzeń systemu.</span><span class="sxs-lookup"><span data-stu-id="b082a-319">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="b082a-320">Ta metoda wywołuje `SetColorScheme` procedury.</span><span class="sxs-lookup"><span data-stu-id="b082a-320">This method calls the `SetColorScheme` procedure.</span></span>  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5. <span data-ttu-id="b082a-321">Dodaj kod do formularza <xref:System.Windows.Forms.Control.Dispose%2A> metoda przed wywołaniem do <xref:System.Windows.Forms.Control.Dispose%2A> metody klasy bazowej, aby zwolnić zdarzenia po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b082a-321">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="b082a-322">Aby uzyskać dostęp do <xref:System.Windows.Forms.Control.Dispose%2A> metoda w języku Visual Basic, konieczne będzie rozwiń region, kod generowany przez projektanta formularzy Windows etykietą.</span><span class="sxs-lookup"><span data-stu-id="b082a-322">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b082a-323">Kod zdarzenia system działa wątku oddzielnie od głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b082a-323">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="b082a-324">Jeśli zdarzenie nie jest zwolniony, kod, który można dołączyć do zdarzenia będzie działać po zamknięciu programu.</span><span class="sxs-lookup"><span data-stu-id="b082a-324">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6. <span data-ttu-id="b082a-325">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b082a-325">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="b082a-326">Przekazywania ważnych informacji przy użyciu metod innych niż dźwięku</span><span class="sxs-lookup"><span data-stu-id="b082a-326">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="b082a-327">W tej aplikacji żadne informacje jest przekazywany za pomocą samodzielnie dźwięku.</span><span class="sxs-lookup"><span data-stu-id="b082a-327">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="b082a-328">Jeśli używasz dźwięk w aplikacji należy dostarczać informacji za pomocą innych środków także.</span><span class="sxs-lookup"><span data-stu-id="b082a-328">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="b082a-329">Aby podać informacje w inny sposób niż dźwięku</span><span class="sxs-lookup"><span data-stu-id="b082a-329">To supply information by some other means than sound</span></span>  
  
1. <span data-ttu-id="b082a-330">Należy na pasku tytułu flash przy użyciu funkcji Windows API FlashWindow.</span><span class="sxs-lookup"><span data-stu-id="b082a-330">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="b082a-331">Na przykład sposób wywołania funkcji Windows API zobacz [instruktażu: Wywoływanie Windows API](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="b082a-331">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b082a-332">Użytkownik może korzystać z usługi Windows WartownikDźwięków włączone, co spowoduje również okna flash odtwarzania dźwięki systemu za pomocą wbudowanych głośników komputera.</span><span class="sxs-lookup"><span data-stu-id="b082a-332">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2. <span data-ttu-id="b082a-333">Wyświetlania ważnych informacji w kompaktowym niemodalnym oknie, dzięki czemu użytkownik może odpowiedzieć na.</span><span class="sxs-lookup"><span data-stu-id="b082a-333">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3. <span data-ttu-id="b082a-334">Wyświetla okno komunikatu, który uzyskuje fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="b082a-334">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="b082a-335">Należy unikać tej metody, gdy użytkownik może wpisać.</span><span class="sxs-lookup"><span data-stu-id="b082a-335">Avoid this method when the user may be typing.</span></span>  
  
4. <span data-ttu-id="b082a-336">Wyświetl wskaźnik stanu w obszarze stanu powiadomień paska zadań.</span><span class="sxs-lookup"><span data-stu-id="b082a-336">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="b082a-337">Aby uzyskać więcej informacji, zobacz [dodawanie ikon aplikacji do paska zadań za pomocą składnika NotifyIcon formularzy Windows](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="b082a-337">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="b082a-338">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b082a-338">Testing the Application</span></span>  
 <span data-ttu-id="b082a-339">Przed wdrożeniem aplikacji, należy przetestować funkcje ułatwień dostępu, które zostały zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="b082a-339">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="b082a-340">Aby przetestować funkcje ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="b082a-340">To test accessibility features</span></span>  
  
1. <span data-ttu-id="b082a-341">Aby przetestować dostęp za pomocą klawiatury, odłącz myszy, a następnie przejdź do interfejsu użytkownika dla każdej funkcji, za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="b082a-341">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="b082a-342">Upewnij się, że wszystkie zadania można wykonać za pomocą klawiatury, tylko.</span><span class="sxs-lookup"><span data-stu-id="b082a-342">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2. <span data-ttu-id="b082a-343">Aby przetestować obsługę dużego kontrastu, wybierz ikonę aplet Opcje ułatwień dostępu w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="b082a-343">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="b082a-344">Kliknij kartę ekran, a następnie zaznacz pole wyboru Użyj o wysokim kontraście.</span><span class="sxs-lookup"><span data-stu-id="b082a-344">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="b082a-345">Przejdź do wszystkich elementów interfejsu użytkownika, aby upewnić się, że odzwierciedlenie zmiany kolorów i czcionek.</span><span class="sxs-lookup"><span data-stu-id="b082a-345">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="b082a-346">Ponadto upewnij się, obrazów lub wzorców rysowane pod tekstem zostaną pominięte.</span><span class="sxs-lookup"><span data-stu-id="b082a-346">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b082a-347">Windows NT 4 nie ma ikony opcji ułatwień dostępu w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="b082a-347">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="b082a-348">W związku z tym tę procedurę dla zmiany ustawienia SystemInformation.HighContrast nie działa w Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="b082a-348">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3. <span data-ttu-id="b082a-349">Inne narzędzia są łatwo dostępne dla testów dostępności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b082a-349">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4. <span data-ttu-id="b082a-350">Aby przetestować udostępnianie fokus klawiatury, uruchom program Lupa.</span><span class="sxs-lookup"><span data-stu-id="b082a-350">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="b082a-351">(Aby go otworzyć, kliknij przycisk **Start** menu wskaż **programy**, wskaż polecenie **Akcesoria**, wskaż **ułatwień dostępu**, a następnie kliknij przycisk  **Program Lupa**).</span><span class="sxs-lookup"><span data-stu-id="b082a-351">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="b082a-352">Przejdź interfejsu użytkownika przy użyciu przełączania klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="b082a-352">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="b082a-353">Upewnij się poprawnie w systemie śledzenia wszystkich nawigacji **Lupa**.</span><span class="sxs-lookup"><span data-stu-id="b082a-353">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5. <span data-ttu-id="b082a-354">Aby przetestować uwidaczniającą elementów na ekranie, uruchom Sprawdź, a następnie użyj myszy i klawisz TAB, aby dotrzeć do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="b082a-354">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="b082a-355">Upewnij się, że informacje znajdujące się w polach Nazwa, stan, rola, lokalizacji i wartość okna Sprawdź zrozumiały dla użytkownika dla każdego obiektu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b082a-355">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
