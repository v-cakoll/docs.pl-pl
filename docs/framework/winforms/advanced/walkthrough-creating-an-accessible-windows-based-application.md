---
title: "Wskazówki: tworzenie dostępnej aplikacji bazującej na systemie Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8f0a35b569b38e0d7ca79129f720034420ecd23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="4410d-102">Wskazówki: tworzenie dostępnej aplikacji bazującej na systemie Windows</span><span class="sxs-lookup"><span data-stu-id="4410d-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="4410d-103">Tworzenie aplikacji dostępny implikacje ważnymi.</span><span class="sxs-lookup"><span data-stu-id="4410d-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="4410d-104">Wiele rządy ma przepisy dotyczące ułatwień dostępu dla zakupów oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="4410d-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="4410d-105">Logo Certified for Windows zawiera wymagania dotyczące ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="4410d-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="4410d-106">Szacowany mieszkańców 30 milionów intruzowi US, ile z nich potencjalnych klientów, mają wpływu na dostępność oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="4410d-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="4410d-107">W tym przewodniku zajmie się pięć wymagania związane z dostępem do logo Certified for Windows.</span><span class="sxs-lookup"><span data-stu-id="4410d-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="4410d-108">Zgodnie z tych wymagań będzie dostępny aplikacji:</span><span class="sxs-lookup"><span data-stu-id="4410d-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="4410d-109">Obsługuje rozmiar panelu sterowania, kolorów, czcionki i wprowadź ustawienia.</span><span class="sxs-lookup"><span data-stu-id="4410d-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="4410d-110">Paska menu, paska tytułu, obramowania i paska stanu spowoduje wszystkie zmiany rozmiaru się gdy użytkownik zmieni ustawienia Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="4410d-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="4410d-111">W tej aplikacji nie są konieczne nie dodatkowe zmiany do formantów lub kodu.</span><span class="sxs-lookup"><span data-stu-id="4410d-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="4410d-112">Obsługuje tryb dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="4410d-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="4410d-113">Podaj klawiaturę udokumentowaną dostęp do wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="4410d-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="4410d-114">Udostępnianie lokalizacji fokus klawiatury ModelID.</span><span class="sxs-lookup"><span data-stu-id="4410d-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="4410d-115">Unikaj przekazywania ważnych informacji przez samego dźwięku.</span><span class="sxs-lookup"><span data-stu-id="4410d-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="4410d-116">Aby uzyskać więcej informacji, zobacz [zasoby do projektowania dostępnych aplikacji](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="4410d-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="4410d-117">Aby uzyskać informacje dotyczące obsługi różnych układów klawiatury, zobacz [najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="4410d-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="4410d-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="4410d-118">Creating the Project</span></span>  
 <span data-ttu-id="4410d-119">W tym przewodniku tworzy interfejsu użytkownika dla aplikacji, która przyjmuje pizza zleceń.</span><span class="sxs-lookup"><span data-stu-id="4410d-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="4410d-120">Składa się z <xref:System.Windows.Forms.TextBox> dla nazwy klienta <xref:System.Windows.Forms.RadioButton> grupy, aby wybrać rozmiar pizza <xref:System.Windows.Forms.CheckedListBox> doboru toppings dwóch formantów przycisk etykietą kolejności i Anuluj i Menu za pomocą wiersza polecenia zakończenia.</span><span class="sxs-lookup"><span data-stu-id="4410d-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="4410d-121">Użytkownik wprowadza nazwę klienta, rozmiar pizza i toppings potrzeby.</span><span class="sxs-lookup"><span data-stu-id="4410d-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="4410d-122">Gdy użytkownik kliknie przycisk kolejność, podsumowanie kolejność i jego koszty są wyświetlane w oknie komunikatu i formanty są wyczyszczone i jest gotowa do następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4410d-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="4410d-123">Gdy użytkownik kliknie przycisk Anuluj, formanty są wyczyszczone i jest gotowa do następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4410d-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="4410d-124">Po kliknięciu elementu menu zakończenia zamyka program.</span><span class="sxs-lookup"><span data-stu-id="4410d-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="4410d-125">Nacisk ten przewodnik nie jest kod systemu kolejności detaliczne, ale ułatwień dostępu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4410d-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="4410d-126">Funkcje ułatwień dostępu w kilku często używanych formantów, w tym przyciski, przyciski radiowe pola tekstowe i etykiety przedstawiono wskazówki.</span><span class="sxs-lookup"><span data-stu-id="4410d-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="4410d-127">Aby rozpocząć tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4410d-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="4410d-128">Utwórz nową aplikację systemu Windows w [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4410d-128">Create a new Windows Application in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="4410d-129">Nazwij projekt **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="4410d-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="4410d-130">(Aby uzyskać więcej informacji, zobacz [tworzenie nowych rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="4410d-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="4410d-131">Dodawanie formantów do formularza</span><span class="sxs-lookup"><span data-stu-id="4410d-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="4410d-132">Gdy dodawanie formantów do formularza, należy pamiętać, aby aplikacja dostępne poniższe wskazówki:</span><span class="sxs-lookup"><span data-stu-id="4410d-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="4410d-133">Ustaw <xref:System.Windows.Forms.Control.AccessibleDescription%2A> i <xref:System.Windows.Forms.Control.AccessibleName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4410d-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="4410d-134">W tym przykładzie ustawienie domyślne <xref:System.Windows.Forms.Control.AccessibleRole%2A> jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="4410d-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="4410d-135">Aby uzyskać więcej informacji na temat właściwości ułatwień dostępu, zobacz [dostarczanie informacji dotyczących ułatwień dostępu dla formantów w formularzu systemu Windows](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="4410d-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="4410d-136">Ustaw rozmiar czcionki, do 10 punktów lub większy.</span><span class="sxs-lookup"><span data-stu-id="4410d-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4410d-137">Jeśli ustawisz rozmiar czcionki w postaci 10 podczas uruchamiania, wszystkie formanty dodane do formularza będzie mieć rozmiar czcionki 10.</span><span class="sxs-lookup"><span data-stu-id="4410d-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="4410d-138">Upewnij się, że wszelkie formant etykiety, który opisuje kontrolki pola tekstowego bezpośrednio poprzedza formantu TextBox w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="4410d-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="4410d-139">Dodaj klucz dostępu za pomocą znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> żadnego formantu, użytkownik może chcieć przejdź do właściwości.</span><span class="sxs-lookup"><span data-stu-id="4410d-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="4410d-140">Dodaj klucz dostępu za pomocą znaku "&", do <xref:System.Windows.Forms.Control.Text%2A> właściwości poprzedzający formant, który użytkownik może chcieć przejdź do etykiety.</span><span class="sxs-lookup"><span data-stu-id="4410d-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="4410d-141">Ustaw etykiet <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwości `true`, dzięki czemu fokus jest ustawiony do następnego formantu w kolejności tabulacji, gdy użytkownik naciśnie klawisz dostępu.</span><span class="sxs-lookup"><span data-stu-id="4410d-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="4410d-142">Dodaj klucze dostępu do wszystkich elementów menu.</span><span class="sxs-lookup"><span data-stu-id="4410d-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="4410d-143">Aby udostępnić aplikację systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4410d-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="4410d-144">Dodawanie formantów do formularza i ustaw właściwości, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="4410d-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="4410d-145">Zobacz obraz na koniec tabeli dla modeli sposób rozmieszczenia kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="4410d-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="4410d-146">Obiekt</span><span class="sxs-lookup"><span data-stu-id="4410d-146">Object</span></span>|<span data-ttu-id="4410d-147">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4410d-147">Property</span></span>|<span data-ttu-id="4410d-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="4410d-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="4410d-149">Form1</span><span class="sxs-lookup"><span data-stu-id="4410d-149">Form1</span></span>|<span data-ttu-id="4410d-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-150">AccessibleDescription</span></span>|<span data-ttu-id="4410d-151">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="4410d-151">Order form</span></span>|  
    ||<span data-ttu-id="4410d-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-152">AccessibleName</span></span>|<span data-ttu-id="4410d-153">Formularz zamówienia</span><span class="sxs-lookup"><span data-stu-id="4410d-153">Order form</span></span>|  
    ||<span data-ttu-id="4410d-154">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="4410d-154">Font Size</span></span>|<span data-ttu-id="4410d-155">10</span><span class="sxs-lookup"><span data-stu-id="4410d-155">10</span></span>|  
    ||<span data-ttu-id="4410d-156">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-156">Text</span></span>|<span data-ttu-id="4410d-157">Formularz zamawiania pizzy</span><span class="sxs-lookup"><span data-stu-id="4410d-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="4410d-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="4410d-158">PictureBox</span></span>|<span data-ttu-id="4410d-159">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-159">Name</span></span>|<span data-ttu-id="4410d-160">logo</span><span class="sxs-lookup"><span data-stu-id="4410d-160">logo</span></span>|  
    ||<span data-ttu-id="4410d-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-161">AccessibleDescription</span></span>|<span data-ttu-id="4410d-162">Wycinek pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="4410d-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-163">AccessibleName</span></span>|<span data-ttu-id="4410d-164">Logo firmy</span><span class="sxs-lookup"><span data-stu-id="4410d-164">Company logo</span></span>|  
    ||<span data-ttu-id="4410d-165">Obraz</span><span class="sxs-lookup"><span data-stu-id="4410d-165">Image</span></span>|<span data-ttu-id="4410d-166">Wszystkie ikony lub mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="4410d-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="4410d-167">Etykieta</span><span class="sxs-lookup"><span data-stu-id="4410d-167">Label</span></span>|<span data-ttu-id="4410d-168">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-168">Name</span></span>|<span data-ttu-id="4410d-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="4410d-169">companyLabel</span></span>|  
    ||<span data-ttu-id="4410d-170">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-170">Text</span></span>|<span data-ttu-id="4410d-171">Dobrym Pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="4410d-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-172">TabIndex</span></span>|<span data-ttu-id="4410d-173">1</span><span class="sxs-lookup"><span data-stu-id="4410d-173">1</span></span>|  
    ||<span data-ttu-id="4410d-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-174">AccessibleDescription</span></span>|<span data-ttu-id="4410d-175">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="4410d-175">Company name</span></span>|  
    ||<span data-ttu-id="4410d-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-176">AccessibleName</span></span>|<span data-ttu-id="4410d-177">Nazwa firmy</span><span class="sxs-lookup"><span data-stu-id="4410d-177">Company name</span></span>|  
    ||<span data-ttu-id="4410d-178">Kolor tła</span><span class="sxs-lookup"><span data-stu-id="4410d-178">Backcolor</span></span>|<span data-ttu-id="4410d-179">niebieski</span><span class="sxs-lookup"><span data-stu-id="4410d-179">Blue</span></span>|  
    ||<span data-ttu-id="4410d-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="4410d-180">Forecolor</span></span>|<span data-ttu-id="4410d-181">żółty</span><span class="sxs-lookup"><span data-stu-id="4410d-181">Yellow</span></span>|  
    ||<span data-ttu-id="4410d-182">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="4410d-182">Font size</span></span>|<span data-ttu-id="4410d-183">18</span><span class="sxs-lookup"><span data-stu-id="4410d-183">18</span></span>|  
    |<span data-ttu-id="4410d-184">Etykieta</span><span class="sxs-lookup"><span data-stu-id="4410d-184">Label</span></span>|<span data-ttu-id="4410d-185">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-185">Name</span></span>|<span data-ttu-id="4410d-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="4410d-186">customerLabel</span></span>|  
    ||<span data-ttu-id="4410d-187">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-187">Text</span></span>|<span data-ttu-id="4410d-188">& Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-188">&Name</span></span>|  
    ||<span data-ttu-id="4410d-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-189">TabIndex</span></span>|<span data-ttu-id="4410d-190">2</span><span class="sxs-lookup"><span data-stu-id="4410d-190">2</span></span>|  
    ||<span data-ttu-id="4410d-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-191">AccessibleDescription</span></span>|<span data-ttu-id="4410d-192">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="4410d-192">Customer name label</span></span>|  
    ||<span data-ttu-id="4410d-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-193">AccessibleName</span></span>|<span data-ttu-id="4410d-194">Etykieta nazwy klienta</span><span class="sxs-lookup"><span data-stu-id="4410d-194">Customer name label</span></span>|  
    ||<span data-ttu-id="4410d-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="4410d-195">UseMnemonic</span></span>|<span data-ttu-id="4410d-196">Wartość true</span><span class="sxs-lookup"><span data-stu-id="4410d-196">True</span></span>|  
    |<span data-ttu-id="4410d-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="4410d-197">TextBox</span></span>|<span data-ttu-id="4410d-198">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-198">Name</span></span>|<span data-ttu-id="4410d-199">CustomerName</span><span class="sxs-lookup"><span data-stu-id="4410d-199">customerName</span></span>|  
    ||<span data-ttu-id="4410d-200">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-200">Text</span></span>|<span data-ttu-id="4410d-201">(Brak)</span><span class="sxs-lookup"><span data-stu-id="4410d-201">(none)</span></span>|  
    ||<span data-ttu-id="4410d-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-202">TabIndex</span></span>|<span data-ttu-id="4410d-203">3</span><span class="sxs-lookup"><span data-stu-id="4410d-203">3</span></span>|  
    ||<span data-ttu-id="4410d-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-204">AccessibleDescription</span></span>|<span data-ttu-id="4410d-205">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="4410d-205">Customer name</span></span>|  
    ||<span data-ttu-id="4410d-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-206">AccessibleName</span></span>|<span data-ttu-id="4410d-207">Nazwa klienta</span><span class="sxs-lookup"><span data-stu-id="4410d-207">Customer name</span></span>|  
    |<span data-ttu-id="4410d-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="4410d-208">GroupBox</span></span>|<span data-ttu-id="4410d-209">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-209">Name</span></span>|<span data-ttu-id="4410d-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="4410d-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="4410d-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-211">AccessibleDescription</span></span>|<span data-ttu-id="4410d-212">Opcje rozmiaru pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="4410d-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-213">AccessibleName</span></span>|<span data-ttu-id="4410d-214">Opcje rozmiaru pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="4410d-215">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-215">Text</span></span>|<span data-ttu-id="4410d-216">Rozmiar pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-216">Pizza size</span></span>|  
    ||<span data-ttu-id="4410d-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-217">TabIndex</span></span>|<span data-ttu-id="4410d-218">4</span><span class="sxs-lookup"><span data-stu-id="4410d-218">4</span></span>|  
    |<span data-ttu-id="4410d-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4410d-219">RadioButton</span></span>|<span data-ttu-id="4410d-220">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-220">Name</span></span>|<span data-ttu-id="4410d-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="4410d-221">smallPizza</span></span>|  
    ||<span data-ttu-id="4410d-222">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-222">Text</span></span>|<span data-ttu-id="4410d-223">& małe $6,00</span><span class="sxs-lookup"><span data-stu-id="4410d-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="4410d-224">Zaznaczone</span><span class="sxs-lookup"><span data-stu-id="4410d-224">Checked</span></span>|<span data-ttu-id="4410d-225">Wartość true</span><span class="sxs-lookup"><span data-stu-id="4410d-225">True</span></span>|  
    ||<span data-ttu-id="4410d-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-226">TabIndex</span></span>|<span data-ttu-id="4410d-227">0</span><span class="sxs-lookup"><span data-stu-id="4410d-227">0</span></span>|  
    ||<span data-ttu-id="4410d-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-228">AccessibleDescription</span></span>|<span data-ttu-id="4410d-229">Mała pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-229">Small pizza</span></span>|  
    ||<span data-ttu-id="4410d-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-230">AccessibleName</span></span>|<span data-ttu-id="4410d-231">Mała pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-231">Small pizza</span></span>|  
    |<span data-ttu-id="4410d-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4410d-232">RadioButton</span></span>|<span data-ttu-id="4410d-233">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-233">Name</span></span>|<span data-ttu-id="4410d-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="4410d-234">largePizza</span></span>|  
    ||<span data-ttu-id="4410d-235">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-235">Text</span></span>|<span data-ttu-id="4410d-236">& dużych $10,00</span><span class="sxs-lookup"><span data-stu-id="4410d-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="4410d-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-237">TabIndex</span></span>|<span data-ttu-id="4410d-238">1</span><span class="sxs-lookup"><span data-stu-id="4410d-238">1</span></span>|  
    ||<span data-ttu-id="4410d-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-239">AccessibleDescription</span></span>|<span data-ttu-id="4410d-240">Wielka pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-240">Large pizza</span></span>|  
    ||<span data-ttu-id="4410d-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-241">AccessibleName</span></span>|<span data-ttu-id="4410d-242">Wielka pizza</span><span class="sxs-lookup"><span data-stu-id="4410d-242">Large pizza</span></span>|  
    |<span data-ttu-id="4410d-243">Etykieta</span><span class="sxs-lookup"><span data-stu-id="4410d-243">Label</span></span>|<span data-ttu-id="4410d-244">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-244">Name</span></span>|<span data-ttu-id="4410d-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="4410d-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="4410d-246">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-246">Text</span></span>|<span data-ttu-id="4410d-247">& toppings ($0,75 każdego)</span><span class="sxs-lookup"><span data-stu-id="4410d-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="4410d-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-248">TabIndex</span></span>|<span data-ttu-id="4410d-249">5</span><span class="sxs-lookup"><span data-stu-id="4410d-249">5</span></span>|  
    ||<span data-ttu-id="4410d-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-250">AccessibleDescription</span></span>|<span data-ttu-id="4410d-251">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="4410d-251">Toppings label</span></span>|  
    ||<span data-ttu-id="4410d-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-252">AccessibleName</span></span>|<span data-ttu-id="4410d-253">Etykieta toppings</span><span class="sxs-lookup"><span data-stu-id="4410d-253">Toppings label</span></span>|  
    ||<span data-ttu-id="4410d-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="4410d-254">UseMnemonic</span></span>|<span data-ttu-id="4410d-255">Wartość true</span><span class="sxs-lookup"><span data-stu-id="4410d-255">True</span></span>|  
    |<span data-ttu-id="4410d-256">CheckedListBox —</span><span class="sxs-lookup"><span data-stu-id="4410d-256">CheckedListBox</span></span>|<span data-ttu-id="4410d-257">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-257">Name</span></span>|<span data-ttu-id="4410d-258">toppings</span><span class="sxs-lookup"><span data-stu-id="4410d-258">toppings</span></span>|  
    ||<span data-ttu-id="4410d-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-259">TabIndex</span></span>|<span data-ttu-id="4410d-260">6</span><span class="sxs-lookup"><span data-stu-id="4410d-260">6</span></span>|  
    ||<span data-ttu-id="4410d-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-261">AccessibleDescription</span></span>|<span data-ttu-id="4410d-262">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="4410d-262">Available toppings</span></span>|  
    ||<span data-ttu-id="4410d-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-263">AccessibleName</span></span>|<span data-ttu-id="4410d-264">Dostępne toppings</span><span class="sxs-lookup"><span data-stu-id="4410d-264">Available toppings</span></span>|  
    ||<span data-ttu-id="4410d-265">Elementy</span><span class="sxs-lookup"><span data-stu-id="4410d-265">Items</span></span>|<span data-ttu-id="4410d-266">Pepperoni, produkcji kiełbas, grzyby</span><span class="sxs-lookup"><span data-stu-id="4410d-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="4410d-267">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4410d-267">Button</span></span>|<span data-ttu-id="4410d-268">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-268">Name</span></span>|<span data-ttu-id="4410d-269">kolejność</span><span class="sxs-lookup"><span data-stu-id="4410d-269">order</span></span>|  
    ||<span data-ttu-id="4410d-270">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-270">Text</span></span>|<span data-ttu-id="4410d-271">& kolejności</span><span class="sxs-lookup"><span data-stu-id="4410d-271">&Order</span></span>|  
    ||<span data-ttu-id="4410d-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-272">TabIndex</span></span>|<span data-ttu-id="4410d-273">7</span><span class="sxs-lookup"><span data-stu-id="4410d-273">7</span></span>|  
    ||<span data-ttu-id="4410d-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-274">AccessibleDescription</span></span>|<span data-ttu-id="4410d-275">Łączna liczba kolejności</span><span class="sxs-lookup"><span data-stu-id="4410d-275">Total the order</span></span>|  
    ||<span data-ttu-id="4410d-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-276">AccessibleName</span></span>|<span data-ttu-id="4410d-277">Kolejność</span><span class="sxs-lookup"><span data-stu-id="4410d-277">Total order</span></span>|  
    |<span data-ttu-id="4410d-278">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4410d-278">Button</span></span>|<span data-ttu-id="4410d-279">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-279">Name</span></span>|<span data-ttu-id="4410d-280">Anuluj</span><span class="sxs-lookup"><span data-stu-id="4410d-280">cancel</span></span>|  
    ||<span data-ttu-id="4410d-281">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-281">Text</span></span>|<span data-ttu-id="4410d-282">& Anuluj</span><span class="sxs-lookup"><span data-stu-id="4410d-282">&Cancel</span></span>|  
    ||<span data-ttu-id="4410d-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="4410d-283">TabIndex</span></span>|<span data-ttu-id="4410d-284">8</span><span class="sxs-lookup"><span data-stu-id="4410d-284">8</span></span>|  
    ||<span data-ttu-id="4410d-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="4410d-285">AccessibleDescription</span></span>|<span data-ttu-id="4410d-286">Anulowanie zamówienia</span><span class="sxs-lookup"><span data-stu-id="4410d-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="4410d-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="4410d-287">AccessibleName</span></span>|<span data-ttu-id="4410d-288">Anulowanie zlecenia</span><span class="sxs-lookup"><span data-stu-id="4410d-288">Cancel order</span></span>|  
    |<span data-ttu-id="4410d-289">MainMenu —</span><span class="sxs-lookup"><span data-stu-id="4410d-289">MainMenu</span></span>|<span data-ttu-id="4410d-290">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-290">Name</span></span>|<span data-ttu-id="4410d-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="4410d-291">theMainMenu</span></span>|  
    |<span data-ttu-id="4410d-292">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="4410d-292">MenuItem</span></span>|<span data-ttu-id="4410d-293">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-293">Name</span></span>|<span data-ttu-id="4410d-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="4410d-294">fileCommands</span></span>|  
    ||<span data-ttu-id="4410d-295">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-295">Text</span></span>|<span data-ttu-id="4410d-296">& pliku</span><span class="sxs-lookup"><span data-stu-id="4410d-296">&File</span></span>|  
    |<span data-ttu-id="4410d-297">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="4410d-297">MenuItem</span></span>|<span data-ttu-id="4410d-298">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4410d-298">Name</span></span>|<span data-ttu-id="4410d-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="4410d-299">exitApp</span></span>|  
    ||<span data-ttu-id="4410d-300">Tekst</span><span class="sxs-lookup"><span data-stu-id="4410d-300">Text</span></span>|<span data-ttu-id="4410d-301">& Zakończ</span><span class="sxs-lookup"><span data-stu-id="4410d-301">E&xit</span></span>|  
  
     <span data-ttu-id="4410d-302">![Formularz zamawiania pizzy](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span><span class="sxs-lookup"><span data-stu-id="4410d-302">![Pizza Order Form](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span></span>  
<span data-ttu-id="4410d-303">Formularz będzie wyglądać jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="4410d-303">Your form will look something like the following:</span></span>  
  
## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="4410d-304">Obsługa w trybie dużego kontrastu</span><span class="sxs-lookup"><span data-stu-id="4410d-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="4410d-305">Wysoki kontrast tryb jest ustawienie systemu Windows, które poprawia czytelność przy użyciu wyraźnych kolorów i rozmiary czcionek, które są przydatne dla użytkowników niedowidzących.</span><span class="sxs-lookup"><span data-stu-id="4410d-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="4410d-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Właściwość jest udostępniana do określenia, czy ustawiono tryb dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="4410d-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="4410d-307">Jeśli jest SystemInformation.HighContrast `true`, powinien aplikacji:</span><span class="sxs-lookup"><span data-stu-id="4410d-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="4410d-308">Wyświetl wszystkie elementy interfejsu użytkownika przy użyciu schemat kolorów systemu</span><span class="sxs-lookup"><span data-stu-id="4410d-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="4410d-309">Przekazuje za pomocą wizualnych lub dźwięk wszystkie informacje, które jest przekazywany za pomocą kolorów.</span><span class="sxs-lookup"><span data-stu-id="4410d-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="4410d-310">Na przykład jeśli wyróżniania elementów określonej listy przy użyciu czcionki czerwony, można również dodaniu pogrubioną czcionką, tak, aby użytkownik miał wskazówki-color wyróżniono elementy.</span><span class="sxs-lookup"><span data-stu-id="4410d-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="4410d-311">Pomiń wszystkie obrazy lub wzorce pod tekstem</span><span class="sxs-lookup"><span data-stu-id="4410d-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="4410d-312">Aplikacja ma sprawdzać ustawienie <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> po aplikacji uruchamia i odpowiadać na zdarzenie systemowe <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="4410d-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="4410d-313"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Zdarzenie jest wywoływane zawsze, gdy wartość <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> zmiany.</span><span class="sxs-lookup"><span data-stu-id="4410d-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="4410d-314">W naszej aplikacji jest jedynym elementem, który nie używa systemowe ustawienia koloru `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="4410d-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="4410d-315"><xref:System.Drawing.SystemColors> Klasa jest używana do zmiany ustawień kolor etykiety kolory wybrane przez użytkownika systemu.</span><span class="sxs-lookup"><span data-stu-id="4410d-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="4410d-316">Aby włączyć tryb dużego kontrastu w sposób</span><span class="sxs-lookup"><span data-stu-id="4410d-316">To enable High Contrast mode in an effective way</span></span>  
  
1.  <span data-ttu-id="4410d-317">Tworzenie metody, aby ustawić kolory etykiety do kolorów systemu.</span><span class="sxs-lookup"><span data-stu-id="4410d-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
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
  
2.  <span data-ttu-id="4410d-318">Wywołanie `SetColorScheme` procedury w Konstruktorze formularza (`Public Sub New()` w języku Visual Basic i `public class Form1` języka Visual C#).</span><span class="sxs-lookup"><span data-stu-id="4410d-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="4410d-319">Aby uzyskać dostęp do konstruktora w języku Visual Basic, konieczne będzie Rozwiń pole oznaczone **kod wygenerowany przez projektanta formularzy systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="4410d-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
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
  
3.  <span data-ttu-id="4410d-320">Utwórz procedurę zdarzenia z odpowiednim podpisem, aby odpowiedzieć na <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4410d-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
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
  
4.  <span data-ttu-id="4410d-321">Dodaj kod konstruktora formularza po wywołaniu `InitializeComponents`, aby Podłączanie procedury zdarzenia zdarzeń systemowych.</span><span class="sxs-lookup"><span data-stu-id="4410d-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="4410d-322">Ta metoda wywołuje `SetColorScheme` procedury.</span><span class="sxs-lookup"><span data-stu-id="4410d-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
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
  
5.  <span data-ttu-id="4410d-323">Dodaj kod, aby formularz <xref:System.Windows.Forms.Control.Dispose%2A> przed wywołaniem metody <xref:System.Windows.Forms.Control.Dispose%2A> metody klasy podstawowej, aby zwolnić zdarzeń po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4410d-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="4410d-324">Aby uzyskać dostęp do <xref:System.Windows.Forms.Control.Dispose%2A> metody w języku Visual Basic, konieczne będzie Rozwiń pole oznaczone kod generowany przez projektanta formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4410d-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4410d-325">Kod zdarzeń systemu działa niezależnie od aplikacji głównej wątku.</span><span class="sxs-lookup"><span data-stu-id="4410d-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="4410d-326">Jeśli zdarzenie nie zwalnia, kod, który Podłączanie do zdarzeń zostanie uruchomiony, nawet po zamknięciu programu.</span><span class="sxs-lookup"><span data-stu-id="4410d-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
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
  
6.  <span data-ttu-id="4410d-327">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="4410d-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="4410d-328">Ważne informacje w sposób niż dźwięk przekazywania</span><span class="sxs-lookup"><span data-stu-id="4410d-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="4410d-329">W tej aplikacji żadnych informacji przekazywanych dźwięk samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="4410d-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="4410d-330">Jeśli używasz dźwięk w aplikacji, należy określić informacje przy użyciu innych metod również.</span><span class="sxs-lookup"><span data-stu-id="4410d-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="4410d-331">Aby podać informacje w inny sposób niż dźwięku</span><span class="sxs-lookup"><span data-stu-id="4410d-331">To supply information by some other means than sound</span></span>  
  
1.  <span data-ttu-id="4410d-332">Pasek tytułu flash za pomocą funkcji Windows API FlashWindow.</span><span class="sxs-lookup"><span data-stu-id="4410d-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="4410d-333">Przykład wywołania funkcji API systemu Windows, temacie [wskazówki: wywoływanie Windows API](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="4410d-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4410d-334">Użytkownik może korzystać z usługi WartownikDźwięków Windows włączone, co spowoduje również okna flash podczas odtwarzania dźwięki systemu za pośrednictwem wbudowanego prelegenta komputera.</span><span class="sxs-lookup"><span data-stu-id="4410d-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2.  <span data-ttu-id="4410d-335">Wyświetlanie ważne informacje w oknie niemodalne, dzięki czemu użytkownik może odpowiadać na go.</span><span class="sxs-lookup"><span data-stu-id="4410d-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3.  <span data-ttu-id="4410d-336">Wyświetlany komunikat, który uzyskuje fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="4410d-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="4410d-337">Unikaj tej metody, gdy użytkownik może wpisać.</span><span class="sxs-lookup"><span data-stu-id="4410d-337">Avoid this method when the user may be typing.</span></span>  
  
4.  <span data-ttu-id="4410d-338">Wyświetlanie wskaźnika stanu w obszarze powiadomień stanu na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="4410d-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="4410d-339">Aby uzyskać więcej informacji, zobacz [dodawanie ikon aplikacji do elementu TaskBar za pomocą składnika NotifyIcon formularzy systemu Windows](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="4410d-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="4410d-340">Testowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4410d-340">Testing the Application</span></span>  
 <span data-ttu-id="4410d-341">Przed wdrożeniem aplikacji, należy przetestować funkcje ułatwień dostępu, które zostały zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="4410d-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="4410d-342">Aby przetestować funkcje ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="4410d-342">To test accessibility features</span></span>  
  
1.  <span data-ttu-id="4410d-343">Aby przetestować dostęp za pomocą klawiatury, odłącz myszy, a następnie przejdź interfejsu użytkownika dla każdej funkcji za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="4410d-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="4410d-344">Upewnij się, że wszystkie zadania może być wykonana przy użyciu tylko klawiatury.</span><span class="sxs-lookup"><span data-stu-id="4410d-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2.  <span data-ttu-id="4410d-345">Aby przetestować Obsługa dużego kontrastu, wybierz ikonę Opcje ułatwień dostępu w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="4410d-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="4410d-346">Kliknij kartę Wyświetlanie i zaznacz pole wyboru Użyj dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="4410d-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="4410d-347">Przejdź przez wszystkie elementy interfejsu użytkownika, aby upewnić się, że zmiany kolorów i czcionek są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="4410d-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="4410d-348">Upewnij się również, obrazy lub wzorce rysowane pod tekstem zostaną pominięte.</span><span class="sxs-lookup"><span data-stu-id="4410d-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4410d-349">Windows NT 4 nie ma ikony Opcje ułatwień dostępu w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="4410d-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="4410d-350">W związku z tym tej procedury do zmiany ustawień SystemInformation.HighContrast nie działa w systemie Windows NT 4.</span><span class="sxs-lookup"><span data-stu-id="4410d-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3.  <span data-ttu-id="4410d-351">Inne narzędzia są dostępne do testowania dostępności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4410d-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4.  <span data-ttu-id="4410d-352">Aby przetestować udostępnianie fokus klawiatury, uruchom program Lupa.</span><span class="sxs-lookup"><span data-stu-id="4410d-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="4410d-353">(Aby go otworzyć, kliknij przycisk **Start** menu wskaż **programy**, wskaż **Akcesoria**, wskaż **ułatwień dostępu**, a następnie kliknij przycisk  **Program Lupa**).</span><span class="sxs-lookup"><span data-stu-id="4410d-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="4410d-354">Przejdź interfejsu użytkownika za pomocą klawisza TAB klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="4410d-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="4410d-355">Upewnij się, że wszystkie nawigacji jest śledzony poprawnie w **Lupa**.</span><span class="sxs-lookup"><span data-stu-id="4410d-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5.  <span data-ttu-id="4410d-356">Aby przetestować uwidaczniającą elementów ekranu, uruchom inspekcję i używane zarówno mysz, jak i klawisza TAB do osiągnięcia każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="4410d-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="4410d-357">Upewnij się, że informacje przedstawione w polach Nazwa, stan roli, lokalizacji i wartość okna inspekcja jest zrozumiały dla użytkownika, dla każdego obiektu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4410d-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
