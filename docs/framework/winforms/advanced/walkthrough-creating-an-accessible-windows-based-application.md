---
title: 'Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: e7bc996c3d64c0ea3ac8fca5fef759ad309f2967
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336658"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="cd49d-102">Przewodnik: Tworzenie dostępnej aplikacji bazującej na systemie Windows</span><span class="sxs-lookup"><span data-stu-id="cd49d-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="cd49d-103">Tworzenie dostępnej aplikacji ma skutki dla firmy ważne.</span><span class="sxs-lookup"><span data-stu-id="cd49d-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="cd49d-104">Wiele rządy mieć ułatwień dostępu przepisami lub ustaleniami dotyczącymi oprogramowania zakupionego.</span><span class="sxs-lookup"><span data-stu-id="cd49d-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="cd49d-105">Logo Certified for Windows zawiera wymagania dotyczące ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="cd49d-106">Szacowany mieszkańcy 30 mln Stanów Zjednoczonych samodzielnie, wiele potencjalnych klientów, są zagrożone dostępność oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="cd49d-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="cd49d-107">Ten przewodnik pozwala sprostać pięć wymagania dotyczące ułatwień dostępu, logo Certified for Windows.</span><span class="sxs-lookup"><span data-stu-id="cd49d-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="cd49d-108">Zgodnie z tymi wymaganiami dostępnej aplikacji wykonują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cd49d-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="cd49d-109">Obsługuje rozmiar panelu sterowania, kolory, czcionki i wprowadź ustawienia.</span><span class="sxs-lookup"><span data-stu-id="cd49d-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="cd49d-110">Pasek menu, pasek tytułu, obramowania i pasek stanu będzie wszystkie rozmiar się po użytkownik zmienia ustawienia Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="cd49d-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="cd49d-111">Nie dodatkowe zmiany do kontrolki lub kodu są wymagane w tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd49d-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="cd49d-112">Obsługa trybu wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="cd49d-113">Podaj udokumentowanego klawiatury dostęp do wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="cd49d-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="cd49d-114">Udostępnianie lokalizacji fokus klawiatury ModelID.</span><span class="sxs-lookup"><span data-stu-id="cd49d-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="cd49d-115">Należy unikać przekazywania ważnych informacji za pomocą dźwięku samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="cd49d-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="cd49d-116">Aby uzyskać więcej informacji, zobacz [zasoby do projektowania dostępnych aplikacji](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="cd49d-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="cd49d-117">Aby uzyskać informacje dotyczące obsługi różnych układów klawiatury, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="cd49d-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="cd49d-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="cd49d-118">Creating the Project</span></span>  
 <span data-ttu-id="cd49d-119">Ten poradnik tworzy interfejsu użytkownika dla aplikacji, która przyjmuje pizza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="cd49d-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="cd49d-120">Składa się z <xref:System.Windows.Forms.TextBox> dla nazwy klienta <xref:System.Windows.Forms.RadioButton> grupy, aby wybrać rozmiar pizza <xref:System.Windows.Forms.CheckedListBox> służąca do wybierania toppings, dwie kontrolki przycisku etykietą, kolejność i Anuluj i Menu przy użyciu polecenia Exit.</span><span class="sxs-lookup"><span data-stu-id="cd49d-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="cd49d-121">Użytkownik wprowadza nazwę klienta, rozmiar pizza i toppings żądanego.</span><span class="sxs-lookup"><span data-stu-id="cd49d-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="cd49d-122">Gdy użytkownik kliknie przycisk Zamówienie, podsumowanie kolejności i jego kosztów są wyświetlane w oknie komunikatu i formanty są wyczyszczone i jest gotowa do następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="cd49d-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="cd49d-123">Gdy użytkownik kliknie przycisk Anuluj, formanty są wyczyszczone i jest gotowa do następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="cd49d-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="cd49d-124">Gdy użytkownik kliknie element menu zakończenia, zamyka program.</span><span class="sxs-lookup"><span data-stu-id="cd49d-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="cd49d-125">Szczególnym w tym przewodniku nie jest w kodzie system zamówień sprzedaży detalicznej, ale dostępność interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cd49d-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="cd49d-126">Instruktaż demonstruje funkcje ułatwień dostępu kilka często używanych formantów, w tym przycisków, przyciski radiowe, pola tekstowe i etykiety.</span><span class="sxs-lookup"><span data-stu-id="cd49d-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="cd49d-127">Aby rozpocząć tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="cd49d-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="cd49d-128">Utwórz nową aplikację Windows w języku Visual Basic lub Visual C#.</span><span class="sxs-lookup"><span data-stu-id="cd49d-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="cd49d-129">Nadaj projektowi nazwę **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="cd49d-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="cd49d-130">(Aby uzyskać szczegółowe informacje, zobacz [tworzenie nowych rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="cd49d-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="cd49d-131">Dodawanie formantów do formularza</span><span class="sxs-lookup"><span data-stu-id="cd49d-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="cd49d-132">Podczas dodawania formantów do formularza, należy pamiętać, poniższe wskazówki umożliwiają dostępnej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="cd49d-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="cd49d-133">Ustaw <xref:System.Windows.Forms.Control.AccessibleDescription%2A> i <xref:System.Windows.Forms.Control.AccessibleName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd49d-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="cd49d-134">W tym przykładzie domyślne ustawienie dla <xref:System.Windows.Forms.Control.AccessibleRole%2A> jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="cd49d-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="cd49d-135">Aby uzyskać więcej informacji na temat właściwości ułatwień dostępu, zobacz [dostarczanie informacji o ułatwieniach dostępu dla formantów w formularzu Windows](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="cd49d-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="cd49d-136">Ustaw rozmiar czcionki do 10 punktów i większych.</span><span class="sxs-lookup"><span data-stu-id="cd49d-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd49d-137">Jeśli ustawisz rozmiar czcionki w formularzu do 10 podczas uruchamiania, wszystkie kontrolki, następnie dodawane do formularza będzie miał rozmiar czcionki, 10.</span><span class="sxs-lookup"><span data-stu-id="cd49d-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="cd49d-138">Upewnij się, że wszystkie kontrolki etykiety, która opisuje kontrolki TextBox bezpośrednio poprzedza formant pola tekstowego w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="cd49d-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="cd49d-139">Dodaj klucz dostępu, korzystając ze znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> dowolną kontrolkę, użytkownik może chcieć przejść do właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd49d-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="cd49d-140">Dodaj klucz dostępu, korzystając ze znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> właściwość etykiety, który poprzedza formant, który użytkownik może chcieć przejść do.</span><span class="sxs-lookup"><span data-stu-id="cd49d-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="cd49d-141">Ustawić etykiety <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true`, dzięki czemu fokus jest ustawiony do następnej kontrolki w kolejności tabulacji, gdy użytkownik naciśnie klawisz dostępu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="cd49d-142">Dodaj klucze dostępu do wszystkich elementów menu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="cd49d-143">Aby udostępnić aplikację Windows</span><span class="sxs-lookup"><span data-stu-id="cd49d-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="cd49d-144">Dodaj formanty do formularza, a następnie ustaw właściwości, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="cd49d-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="cd49d-145">Zobacz obraz na koniec tabeli dla modeli rozmieszczanie formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="cd49d-146">Obiekt</span><span class="sxs-lookup"><span data-stu-id="cd49d-146">Object</span></span>|<span data-ttu-id="cd49d-147">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cd49d-147">Property</span></span>|<span data-ttu-id="cd49d-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="cd49d-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="cd49d-149">Formularz Form1</span><span class="sxs-lookup"><span data-stu-id="cd49d-149">Form1</span></span>|<span data-ttu-id="cd49d-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-150">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-151">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="cd49d-151">Order form</span></span>|  
    ||<span data-ttu-id="cd49d-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-152">AccessibleName</span></span>|<span data-ttu-id="cd49d-153">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="cd49d-153">Order form</span></span>|  
    ||<span data-ttu-id="cd49d-154">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="cd49d-154">Font Size</span></span>|<span data-ttu-id="cd49d-155">10</span><span class="sxs-lookup"><span data-stu-id="cd49d-155">10</span></span>|  
    ||<span data-ttu-id="cd49d-156">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-156">Text</span></span>|<span data-ttu-id="cd49d-157">Formularz zamówienia pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="cd49d-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="cd49d-158">PictureBox</span></span>|<span data-ttu-id="cd49d-159">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-159">Name</span></span>|<span data-ttu-id="cd49d-160">logo</span><span class="sxs-lookup"><span data-stu-id="cd49d-160">logo</span></span>|  
    ||<span data-ttu-id="cd49d-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-161">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-162">Wycinek pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="cd49d-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-163">AccessibleName</span></span>|<span data-ttu-id="cd49d-164">Logo firmy</span><span class="sxs-lookup"><span data-stu-id="cd49d-164">Company logo</span></span>|  
    ||<span data-ttu-id="cd49d-165">Obraz</span><span class="sxs-lookup"><span data-stu-id="cd49d-165">Image</span></span>|<span data-ttu-id="cd49d-166">Wszystkie ikony lub mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="cd49d-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="cd49d-167">Etykieta</span><span class="sxs-lookup"><span data-stu-id="cd49d-167">Label</span></span>|<span data-ttu-id="cd49d-168">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-168">Name</span></span>|<span data-ttu-id="cd49d-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="cd49d-169">companyLabel</span></span>|  
    ||<span data-ttu-id="cd49d-170">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-170">Text</span></span>|<span data-ttu-id="cd49d-171">Dobre Pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="cd49d-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-172">TabIndex</span></span>|<span data-ttu-id="cd49d-173">1</span><span class="sxs-lookup"><span data-stu-id="cd49d-173">1</span></span>|  
    ||<span data-ttu-id="cd49d-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-174">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-175">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="cd49d-175">Company name</span></span>|  
    ||<span data-ttu-id="cd49d-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-176">AccessibleName</span></span>|<span data-ttu-id="cd49d-177">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="cd49d-177">Company name</span></span>|  
    ||<span data-ttu-id="cd49d-178">Backcolor</span><span class="sxs-lookup"><span data-stu-id="cd49d-178">Backcolor</span></span>|<span data-ttu-id="cd49d-179">Niebieski</span><span class="sxs-lookup"><span data-stu-id="cd49d-179">Blue</span></span>|  
    ||<span data-ttu-id="cd49d-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="cd49d-180">Forecolor</span></span>|<span data-ttu-id="cd49d-181">Żółty</span><span class="sxs-lookup"><span data-stu-id="cd49d-181">Yellow</span></span>|  
    ||<span data-ttu-id="cd49d-182">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="cd49d-182">Font size</span></span>|<span data-ttu-id="cd49d-183">18</span><span class="sxs-lookup"><span data-stu-id="cd49d-183">18</span></span>|  
    |<span data-ttu-id="cd49d-184">Etykieta</span><span class="sxs-lookup"><span data-stu-id="cd49d-184">Label</span></span>|<span data-ttu-id="cd49d-185">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-185">Name</span></span>|<span data-ttu-id="cd49d-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="cd49d-186">customerLabel</span></span>|  
    ||<span data-ttu-id="cd49d-187">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-187">Text</span></span>|<span data-ttu-id="cd49d-188">& Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-188">&Name</span></span>|  
    ||<span data-ttu-id="cd49d-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-189">TabIndex</span></span>|<span data-ttu-id="cd49d-190">2</span><span class="sxs-lookup"><span data-stu-id="cd49d-190">2</span></span>|  
    ||<span data-ttu-id="cd49d-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-191">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-192">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="cd49d-192">Customer name label</span></span>|  
    ||<span data-ttu-id="cd49d-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-193">AccessibleName</span></span>|<span data-ttu-id="cd49d-194">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="cd49d-194">Customer name label</span></span>|  
    ||<span data-ttu-id="cd49d-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="cd49d-195">UseMnemonic</span></span>|<span data-ttu-id="cd49d-196">Prawda</span><span class="sxs-lookup"><span data-stu-id="cd49d-196">True</span></span>|  
    |<span data-ttu-id="cd49d-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="cd49d-197">TextBox</span></span>|<span data-ttu-id="cd49d-198">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-198">Name</span></span>|<span data-ttu-id="cd49d-199">customerName</span><span class="sxs-lookup"><span data-stu-id="cd49d-199">customerName</span></span>|  
    ||<span data-ttu-id="cd49d-200">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-200">Text</span></span>|<span data-ttu-id="cd49d-201">(Brak)</span><span class="sxs-lookup"><span data-stu-id="cd49d-201">(none)</span></span>|  
    ||<span data-ttu-id="cd49d-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-202">TabIndex</span></span>|<span data-ttu-id="cd49d-203">3</span><span class="sxs-lookup"><span data-stu-id="cd49d-203">3</span></span>|  
    ||<span data-ttu-id="cd49d-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-204">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-205">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="cd49d-205">Customer name</span></span>|  
    ||<span data-ttu-id="cd49d-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-206">AccessibleName</span></span>|<span data-ttu-id="cd49d-207">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="cd49d-207">Customer name</span></span>|  
    |<span data-ttu-id="cd49d-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="cd49d-208">GroupBox</span></span>|<span data-ttu-id="cd49d-209">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-209">Name</span></span>|<span data-ttu-id="cd49d-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="cd49d-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="cd49d-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-211">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-212">Opcje rozmiaru pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="cd49d-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-213">AccessibleName</span></span>|<span data-ttu-id="cd49d-214">Opcje rozmiaru pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="cd49d-215">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-215">Text</span></span>|<span data-ttu-id="cd49d-216">Rozmiar pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-216">Pizza size</span></span>|  
    ||<span data-ttu-id="cd49d-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-217">TabIndex</span></span>|<span data-ttu-id="cd49d-218">4</span><span class="sxs-lookup"><span data-stu-id="cd49d-218">4</span></span>|  
    |<span data-ttu-id="cd49d-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="cd49d-219">RadioButton</span></span>|<span data-ttu-id="cd49d-220">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-220">Name</span></span>|<span data-ttu-id="cd49d-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-221">smallPizza</span></span>|  
    ||<span data-ttu-id="cd49d-222">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-222">Text</span></span>|<span data-ttu-id="cd49d-223">& małe $6.00</span><span class="sxs-lookup"><span data-stu-id="cd49d-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="cd49d-224">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="cd49d-224">Checked</span></span>|<span data-ttu-id="cd49d-225">Prawda</span><span class="sxs-lookup"><span data-stu-id="cd49d-225">True</span></span>|  
    ||<span data-ttu-id="cd49d-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-226">TabIndex</span></span>|<span data-ttu-id="cd49d-227">0</span><span class="sxs-lookup"><span data-stu-id="cd49d-227">0</span></span>|  
    ||<span data-ttu-id="cd49d-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-228">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-229">Małe pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-229">Small pizza</span></span>|  
    ||<span data-ttu-id="cd49d-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-230">AccessibleName</span></span>|<span data-ttu-id="cd49d-231">Małe pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-231">Small pizza</span></span>|  
    |<span data-ttu-id="cd49d-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="cd49d-232">RadioButton</span></span>|<span data-ttu-id="cd49d-233">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-233">Name</span></span>|<span data-ttu-id="cd49d-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-234">largePizza</span></span>|  
    ||<span data-ttu-id="cd49d-235">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-235">Text</span></span>|<span data-ttu-id="cd49d-236">& dużych 10,00 zł</span><span class="sxs-lookup"><span data-stu-id="cd49d-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="cd49d-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-237">TabIndex</span></span>|<span data-ttu-id="cd49d-238">1</span><span class="sxs-lookup"><span data-stu-id="cd49d-238">1</span></span>|  
    ||<span data-ttu-id="cd49d-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-239">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-240">Duże pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-240">Large pizza</span></span>|  
    ||<span data-ttu-id="cd49d-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-241">AccessibleName</span></span>|<span data-ttu-id="cd49d-242">Duże pizza</span><span class="sxs-lookup"><span data-stu-id="cd49d-242">Large pizza</span></span>|  
    |<span data-ttu-id="cd49d-243">Etykieta</span><span class="sxs-lookup"><span data-stu-id="cd49d-243">Label</span></span>|<span data-ttu-id="cd49d-244">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-244">Name</span></span>|<span data-ttu-id="cd49d-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="cd49d-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="cd49d-246">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-246">Text</span></span>|<span data-ttu-id="cd49d-247">& toppings ($0,75 każdy)</span><span class="sxs-lookup"><span data-stu-id="cd49d-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="cd49d-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-248">TabIndex</span></span>|<span data-ttu-id="cd49d-249">5</span><span class="sxs-lookup"><span data-stu-id="cd49d-249">5</span></span>|  
    ||<span data-ttu-id="cd49d-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-250">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-251">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="cd49d-251">Toppings label</span></span>|  
    ||<span data-ttu-id="cd49d-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-252">AccessibleName</span></span>|<span data-ttu-id="cd49d-253">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="cd49d-253">Toppings label</span></span>|  
    ||<span data-ttu-id="cd49d-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="cd49d-254">UseMnemonic</span></span>|<span data-ttu-id="cd49d-255">Prawda</span><span class="sxs-lookup"><span data-stu-id="cd49d-255">True</span></span>|  
    |<span data-ttu-id="cd49d-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="cd49d-256">CheckedListBox</span></span>|<span data-ttu-id="cd49d-257">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-257">Name</span></span>|<span data-ttu-id="cd49d-258">toppings</span><span class="sxs-lookup"><span data-stu-id="cd49d-258">toppings</span></span>|  
    ||<span data-ttu-id="cd49d-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-259">TabIndex</span></span>|<span data-ttu-id="cd49d-260">6</span><span class="sxs-lookup"><span data-stu-id="cd49d-260">6</span></span>|  
    ||<span data-ttu-id="cd49d-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-261">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-262">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="cd49d-262">Available toppings</span></span>|  
    ||<span data-ttu-id="cd49d-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-263">AccessibleName</span></span>|<span data-ttu-id="cd49d-264">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="cd49d-264">Available toppings</span></span>|  
    ||<span data-ttu-id="cd49d-265">Elementy</span><span class="sxs-lookup"><span data-stu-id="cd49d-265">Items</span></span>|<span data-ttu-id="cd49d-266">Pepperoni, produkcji kiełbas, grzyby</span><span class="sxs-lookup"><span data-stu-id="cd49d-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="cd49d-267">Przycisk</span><span class="sxs-lookup"><span data-stu-id="cd49d-267">Button</span></span>|<span data-ttu-id="cd49d-268">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-268">Name</span></span>|<span data-ttu-id="cd49d-269">kolejność</span><span class="sxs-lookup"><span data-stu-id="cd49d-269">order</span></span>|  
    ||<span data-ttu-id="cd49d-270">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-270">Text</span></span>|<span data-ttu-id="cd49d-271">& kolejność</span><span class="sxs-lookup"><span data-stu-id="cd49d-271">&Order</span></span>|  
    ||<span data-ttu-id="cd49d-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-272">TabIndex</span></span>|<span data-ttu-id="cd49d-273">7</span><span class="sxs-lookup"><span data-stu-id="cd49d-273">7</span></span>|  
    ||<span data-ttu-id="cd49d-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-274">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-275">Łączna liczba kolejności</span><span class="sxs-lookup"><span data-stu-id="cd49d-275">Total the order</span></span>|  
    ||<span data-ttu-id="cd49d-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-276">AccessibleName</span></span>|<span data-ttu-id="cd49d-277">Zamówienia</span><span class="sxs-lookup"><span data-stu-id="cd49d-277">Total order</span></span>|  
    |<span data-ttu-id="cd49d-278">Przycisk</span><span class="sxs-lookup"><span data-stu-id="cd49d-278">Button</span></span>|<span data-ttu-id="cd49d-279">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-279">Name</span></span>|<span data-ttu-id="cd49d-280">Anuluj</span><span class="sxs-lookup"><span data-stu-id="cd49d-280">cancel</span></span>|  
    ||<span data-ttu-id="cd49d-281">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-281">Text</span></span>|<span data-ttu-id="cd49d-282">& Anuluj</span><span class="sxs-lookup"><span data-stu-id="cd49d-282">&Cancel</span></span>|  
    ||<span data-ttu-id="cd49d-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="cd49d-283">TabIndex</span></span>|<span data-ttu-id="cd49d-284">8</span><span class="sxs-lookup"><span data-stu-id="cd49d-284">8</span></span>|  
    ||<span data-ttu-id="cd49d-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="cd49d-285">AccessibleDescription</span></span>|<span data-ttu-id="cd49d-286">Anulowanie zamówienia</span><span class="sxs-lookup"><span data-stu-id="cd49d-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="cd49d-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="cd49d-287">AccessibleName</span></span>|<span data-ttu-id="cd49d-288">Anulowanie zamówienia</span><span class="sxs-lookup"><span data-stu-id="cd49d-288">Cancel order</span></span>|  
    |<span data-ttu-id="cd49d-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="cd49d-289">MainMenu</span></span>|<span data-ttu-id="cd49d-290">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-290">Name</span></span>|<span data-ttu-id="cd49d-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="cd49d-291">theMainMenu</span></span>|  
    |<span data-ttu-id="cd49d-292">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="cd49d-292">MenuItem</span></span>|<span data-ttu-id="cd49d-293">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-293">Name</span></span>|<span data-ttu-id="cd49d-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="cd49d-294">fileCommands</span></span>|  
    ||<span data-ttu-id="cd49d-295">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-295">Text</span></span>|<span data-ttu-id="cd49d-296">&File</span><span class="sxs-lookup"><span data-stu-id="cd49d-296">&File</span></span>|  
    |<span data-ttu-id="cd49d-297">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="cd49d-297">MenuItem</span></span>|<span data-ttu-id="cd49d-298">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cd49d-298">Name</span></span>|<span data-ttu-id="cd49d-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="cd49d-299">exitApp</span></span>|  
    ||<span data-ttu-id="cd49d-300">Tekst</span><span class="sxs-lookup"><span data-stu-id="cd49d-300">Text</span></span>|<span data-ttu-id="cd49d-301">Za & kończ</span><span class="sxs-lookup"><span data-stu-id="cd49d-301">E&xit</span></span>|
    
      <span data-ttu-id="cd49d-302">Formularz będzie wyglądać podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="cd49d-302">Your form will look something like the following image:</span></span>
    
      ![Formularz kolejności pizza z pola tekstowego, a rozmiar i toppings wybór nazwy.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="cd49d-304">Obsługa trybu wysokiego kontrastu</span><span class="sxs-lookup"><span data-stu-id="cd49d-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="cd49d-305">Trybu wysokiego kontrastu jest ustawienie systemu Windows, który poprawia czytelność przy użyciu kontrastujących i rozmiary czcionek, które są przydatne dla użytkowników niedowidzących.</span><span class="sxs-lookup"><span data-stu-id="cd49d-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="cd49d-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Właściwość została podana w celu ustalenia, czy ustawiono trybu wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="cd49d-307">Jeśli jest SystemInformation.HighContrast `true`, aplikacja powinna:</span><span class="sxs-lookup"><span data-stu-id="cd49d-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="cd49d-308">Wyświetlanie wszystkich elementów interfejsu użytkownika przy użyciu schematu kolorów systemu</span><span class="sxs-lookup"><span data-stu-id="cd49d-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="cd49d-309">Przekazuje za pomocą wizualnych lub dźwięk wszystkie informacje, które jest przekazywane przez kolor.</span><span class="sxs-lookup"><span data-stu-id="cd49d-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="cd49d-310">Na przykład jeśli elementy konkretnej listy są wyróżnione za pomocą czerwonego czcionki, można również dodasz pogrubioną czcionką, tak, aby użytkownik miał cue-color, że elementy są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="cd49d-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="cd49d-311">Pomiń wszelkie obrazy i wzorce pod tekstem</span><span class="sxs-lookup"><span data-stu-id="cd49d-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="cd49d-312">Aplikacja powinna sprawdzać, czy ustawienie <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> podczas uruchamiania aplikacji i odpowiedzieć na zdarzenie systemowe <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="cd49d-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="cd49d-313"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Zdarzenie jest wywoływane zawsze wtedy, gdy wartość <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> zmiany.</span><span class="sxs-lookup"><span data-stu-id="cd49d-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="cd49d-314">W naszej aplikacji jest jedynym elementem, który nie używa ustawień systemowych dla koloru `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="cd49d-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="cd49d-315"><xref:System.Drawing.SystemColors> Klasa jest używana, aby zmienić ustawienia koloru etykiety na kolory systemowe wybrane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cd49d-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="cd49d-316">Aby włączyć tryb dużego kontrastu w skutecznym sposobem</span><span class="sxs-lookup"><span data-stu-id="cd49d-316">To enable High Contrast mode in an effective way</span></span>  
  
1. <span data-ttu-id="cd49d-317">Utwórz metodę, aby ustawić kolory, etykiety kolory systemowe.</span><span class="sxs-lookup"><span data-stu-id="cd49d-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
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
  
2. <span data-ttu-id="cd49d-318">Wywołaj `SetColorScheme` procedury w Konstruktorze formularza (`Public Sub New()` w języku Visual Basic i `public class Form1` w elemencie wizualnym C#).</span><span class="sxs-lookup"><span data-stu-id="cd49d-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="cd49d-319">Aby uzyskać dostęp do konstruktora w języku Visual Basic, konieczne będzie rozwiń region etykietą **kod wygenerowany przez projektanta formularzy Windows**.</span><span class="sxs-lookup"><span data-stu-id="cd49d-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
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
  
3. <span data-ttu-id="cd49d-320">Utwórz procedurę zdarzenia z odpowiednim podpisem, aby odpowiedzieć na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cd49d-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
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
  
4. <span data-ttu-id="cd49d-321">Dodaj kod konstruktora formularza po wywołaniu `InitializeComponents`, żeby podpiąć procedury zdarzenia zdarzeń systemu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="cd49d-322">Ta metoda wywołuje `SetColorScheme` procedury.</span><span class="sxs-lookup"><span data-stu-id="cd49d-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
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
  
5. <span data-ttu-id="cd49d-323">Dodaj kod do formularza <xref:System.Windows.Forms.Control.Dispose%2A> metoda przed wywołaniem do <xref:System.Windows.Forms.Control.Dispose%2A> metody klasy bazowej, aby zwolnić zdarzenia po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd49d-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="cd49d-324">Aby uzyskać dostęp do <xref:System.Windows.Forms.Control.Dispose%2A> metoda w języku Visual Basic, konieczne będzie rozwiń region, kod generowany przez projektanta formularzy Windows etykietą.</span><span class="sxs-lookup"><span data-stu-id="cd49d-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd49d-325">Kod zdarzenia system działa wątku oddzielnie od głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd49d-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="cd49d-326">Jeśli zdarzenie nie jest zwolniony, kod, który można dołączyć do zdarzenia będzie działać po zamknięciu programu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
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
  
6. <span data-ttu-id="cd49d-327">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="cd49d-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="cd49d-328">Przekazywania ważnych informacji przy użyciu metod innych niż dźwięku</span><span class="sxs-lookup"><span data-stu-id="cd49d-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="cd49d-329">W tej aplikacji żadne informacje jest przekazywany za pomocą samodzielnie dźwięku.</span><span class="sxs-lookup"><span data-stu-id="cd49d-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="cd49d-330">Jeśli używasz dźwięk w aplikacji należy dostarczać informacji za pomocą innych środków także.</span><span class="sxs-lookup"><span data-stu-id="cd49d-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="cd49d-331">Aby podać informacje w inny sposób niż dźwięku</span><span class="sxs-lookup"><span data-stu-id="cd49d-331">To supply information by some other means than sound</span></span>  
  
1. <span data-ttu-id="cd49d-332">Należy na pasku tytułu flash przy użyciu funkcji Windows API FlashWindow.</span><span class="sxs-lookup"><span data-stu-id="cd49d-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="cd49d-333">Na przykład sposób wywołania funkcji Windows API zobacz [instruktażu: Wywoływanie Windows API](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="cd49d-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd49d-334">Użytkownik może korzystać z usługi Windows WartownikDźwięków włączone, co spowoduje również okna flash odtwarzania dźwięki systemu za pomocą wbudowanych głośników komputera.</span><span class="sxs-lookup"><span data-stu-id="cd49d-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2. <span data-ttu-id="cd49d-335">Wyświetlania ważnych informacji w kompaktowym niemodalnym oknie, dzięki czemu użytkownik może odpowiedzieć na.</span><span class="sxs-lookup"><span data-stu-id="cd49d-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3. <span data-ttu-id="cd49d-336">Wyświetla okno komunikatu, który uzyskuje fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="cd49d-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="cd49d-337">Należy unikać tej metody, gdy użytkownik może wpisać.</span><span class="sxs-lookup"><span data-stu-id="cd49d-337">Avoid this method when the user may be typing.</span></span>  
  
4. <span data-ttu-id="cd49d-338">Wyświetl wskaźnik stanu w obszarze stanu powiadomień paska zadań.</span><span class="sxs-lookup"><span data-stu-id="cd49d-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="cd49d-339">Aby uzyskać więcej informacji, zobacz [dodawanie ikon aplikacji do paska zadań za pomocą składnika NotifyIcon formularzy Windows](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="cd49d-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="cd49d-340">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="cd49d-340">Testing the Application</span></span>  
 <span data-ttu-id="cd49d-341">Przed wdrożeniem aplikacji, należy przetestować funkcje ułatwień dostępu, które zostały zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="cd49d-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="cd49d-342">Aby przetestować funkcje ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="cd49d-342">To test accessibility features</span></span>  
  
1. <span data-ttu-id="cd49d-343">Aby przetestować dostęp za pomocą klawiatury, odłącz myszy, a następnie przejdź do interfejsu użytkownika dla każdej funkcji, za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="cd49d-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="cd49d-344">Upewnij się, że wszystkie zadania można wykonać za pomocą klawiatury, tylko.</span><span class="sxs-lookup"><span data-stu-id="cd49d-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2. <span data-ttu-id="cd49d-345">Aby przetestować obsługę dużego kontrastu, wybierz ikonę aplet Opcje ułatwień dostępu w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="cd49d-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="cd49d-346">Kliknij kartę ekran, a następnie zaznacz pole wyboru Użyj o wysokim kontraście.</span><span class="sxs-lookup"><span data-stu-id="cd49d-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="cd49d-347">Przejdź do wszystkich elementów interfejsu użytkownika, aby upewnić się, że odzwierciedlenie zmiany kolorów i czcionek.</span><span class="sxs-lookup"><span data-stu-id="cd49d-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="cd49d-348">Ponadto upewnij się, obrazów lub wzorców rysowane pod tekstem zostaną pominięte.</span><span class="sxs-lookup"><span data-stu-id="cd49d-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd49d-349">Windows NT 4 nie ma ikony opcji ułatwień dostępu w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="cd49d-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="cd49d-350">W związku z tym tę procedurę dla zmiany ustawienia SystemInformation.HighContrast nie działa w Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="cd49d-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3. <span data-ttu-id="cd49d-351">Inne narzędzia są łatwo dostępne dla testów dostępności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd49d-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4. <span data-ttu-id="cd49d-352">Aby przetestować udostępnianie fokus klawiatury, uruchom program Lupa.</span><span class="sxs-lookup"><span data-stu-id="cd49d-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="cd49d-353">(Aby go otworzyć, kliknij przycisk **Start** menu wskaż **programy**, wskaż polecenie **Akcesoria**, wskaż **ułatwień dostępu**, a następnie kliknij przycisk  **Program Lupa**).</span><span class="sxs-lookup"><span data-stu-id="cd49d-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="cd49d-354">Przejdź interfejsu użytkownika przy użyciu przełączania klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="cd49d-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="cd49d-355">Upewnij się poprawnie w systemie śledzenia wszystkich nawigacji **Lupa**.</span><span class="sxs-lookup"><span data-stu-id="cd49d-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5. <span data-ttu-id="cd49d-356">Aby przetestować uwidaczniającą elementów na ekranie, uruchom Sprawdź, a następnie użyj myszy i klawisz TAB, aby dotrzeć do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="cd49d-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="cd49d-357">Upewnij się, że informacje znajdujące się w polach Nazwa, stan, rola, lokalizacji i wartość okna Sprawdź zrozumiały dla użytkownika dla każdego obiektu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cd49d-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
