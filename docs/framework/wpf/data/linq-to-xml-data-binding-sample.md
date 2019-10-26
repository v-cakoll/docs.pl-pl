---
title: Przykład powiązania danych LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920938"
---
# <a name="linq-to-xml-data-binding-sample"></a><span data-ttu-id="39900-102">Przykład powiązania danych LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="39900-102">LINQ to XML data binding sample</span></span>

<span data-ttu-id="39900-103">W tym artykule opisano przykład elementu LinqToXmlDataBinding —, aplikację Windows Presentation Foundation (WPF), która wiąże składniki interfejsu użytkownika z osadzonym źródłem danych XML.</span><span class="sxs-lookup"><span data-stu-id="39900-103">This article describes the LinqToXmlDataBinding sample, a Windows Presentation Foundation (WPF) app that binds user interface components to an embedded XML data source.</span></span>

## <a name="overview"></a><span data-ttu-id="39900-104">Omówienie</span><span class="sxs-lookup"><span data-stu-id="39900-104">Overview</span></span>

<span data-ttu-id="39900-105">Przykład elementu LinqToXmlDataBinding — jest aplikacją Windows Presentation Foundation (WPF), która zawiera C# pliki źródłowe XAML i.</span><span class="sxs-lookup"><span data-stu-id="39900-105">The LinqToXmlDataBinding sample is a Windows Presentation Foundation (WPF) app that contains C# and XAML source files.</span></span> <span data-ttu-id="39900-106">Osadzony dokument XML definiuje listę książek.</span><span class="sxs-lookup"><span data-stu-id="39900-106">An embedded XML document defines a list of books.</span></span> <span data-ttu-id="39900-107">Aplikacja umożliwia użytkownikowi wyświetlanie, Dodawanie, usuwanie i edytowanie wpisów książki.</span><span class="sxs-lookup"><span data-stu-id="39900-107">The app enables the user to view, add, delete, and edit the book entries.</span></span>

<span data-ttu-id="39900-108">Istnieją dwa podstawowe pliki źródłowe:</span><span class="sxs-lookup"><span data-stu-id="39900-108">There are two primary source files:</span></span>

- <span data-ttu-id="39900-109">[Kod źródłowy L2DBForm. XAML](l2dbform-xaml-source-code.md) zawiera kod deklaracji XAML dla interfejsu użytkownika okna głównego.</span><span class="sxs-lookup"><span data-stu-id="39900-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contains the XAML declaration code for the user interface (UI) of the main window.</span></span> <span data-ttu-id="39900-110">Zawiera również sekcję zasobów okna, która definiuje dostawcę danych i osadzony dokument XML dla list książek.</span><span class="sxs-lookup"><span data-stu-id="39900-110">It also contains a window resource section that defines a data provider and an embedded XML document for the book listings.</span></span>

- <span data-ttu-id="39900-111">[L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md) zawiera metody inicjowania i obsługi zdarzeń SKOJARZONE z interfejsem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="39900-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contains the initialization and event-handling methods associated with the UI.</span></span>

<span data-ttu-id="39900-112">Okno główne jest podzielone na następujące cztery pionowe sekcje interfejsu użytkownika:</span><span class="sxs-lookup"><span data-stu-id="39900-112">The main window is divided into the following four vertical UI sections:</span></span>

- <span data-ttu-id="39900-113">**Kod XML** Wyświetla pierwotne źródło XML listy osadzonych książek.</span><span class="sxs-lookup"><span data-stu-id="39900-113">**XML** displays the raw XML source of the embedded book listing.</span></span>

- <span data-ttu-id="39900-114">**Lista książek** wyświetla wpisy książki jako tekst standardowy i umożliwia użytkownikowi wybranie i usunięcie poszczególnych wpisów.</span><span class="sxs-lookup"><span data-stu-id="39900-114">**Book List** displays the book entries as standard text and enables the user to select and delete individual entries.</span></span>

- <span data-ttu-id="39900-115">**Edycja wybranej książki** umożliwia użytkownikowi edytowanie wartości skojarzonych z aktualnie wybranym wpisem książki.</span><span class="sxs-lookup"><span data-stu-id="39900-115">**Edit Selected Book** enables the user to edit the values associated with the currently selected book entry.</span></span>

- <span data-ttu-id="39900-116">**Dodawanie nowej książki** umożliwia tworzenie nowych wpisów książki na podstawie wartości wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="39900-116">**Add New Book** enables the creation of a new book entry based on values entered by the user.</span></span>

## <a name="run-the-sample"></a><span data-ttu-id="39900-117">Uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="39900-117">Run the sample</span></span>

<span data-ttu-id="39900-118">W tej sekcji pokazano, jak utworzyć i skompilować projekt elementu LinqToXmlDataBinding — w programie Visual Studio oraz jak uruchomić utworzoną aplikację elementu LinqToXmlDataBinding — Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="39900-118">This section shows how to create and build the LinqToXmlDataBinding project in Visual Studio, and how to run the resulting LinqToXmlDataBinding Windows Presentation Foundation (WPF) app.</span></span>

### <a name="create-the-project"></a><span data-ttu-id="39900-119">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="39900-119">Create the project</span></span>

1. <span data-ttu-id="39900-120">Otwórz program Visual Studio i Utwórz C# **aplikację WPF** o nazwie **elementu LinqToXmlDataBinding —** .</span><span class="sxs-lookup"><span data-stu-id="39900-120">Open Visual Studio and create a C# **WPF App** named **LinqToXmlDataBinding**.</span></span>

   <span data-ttu-id="39900-121">Projekt powinien kierować do .NET Framework 3,5 (lub nowszego).</span><span class="sxs-lookup"><span data-stu-id="39900-121">The project should target the .NET Framework 3.5 (or later).</span></span>

1. <span data-ttu-id="39900-122">Jeśli jeszcze nie istnieje, Dodaj odwołania do projektu dla następujących zestawów .NET:</span><span class="sxs-lookup"><span data-stu-id="39900-122">If not already present, add project references for the following .NET assemblies:</span></span>

    - <span data-ttu-id="39900-123">System.Data</span><span class="sxs-lookup"><span data-stu-id="39900-123">System.Data</span></span>
    - <span data-ttu-id="39900-124">System. Data. DataSetExtensions</span><span class="sxs-lookup"><span data-stu-id="39900-124">System.Data.DataSetExtensions</span></span>
    - <span data-ttu-id="39900-125">System.Xml</span><span class="sxs-lookup"><span data-stu-id="39900-125">System.Xml</span></span>
    - <span data-ttu-id="39900-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="39900-126">System.Xml</span></span>

1. <span data-ttu-id="39900-127">Skompiluj rozwiązanie, naciskając klawisz **Ctrl** +**SHIFT** +**B**, a następnie uruchom go, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="39900-127">Build the solution by pressing **Ctrl**+**Shift**+**B**, then run it by pressing **F5**.</span></span>

   <span data-ttu-id="39900-128">Projekt powinien zostać skompilowany bez błędów i uruchomiony jako ogólna aplikacja WPF.</span><span class="sxs-lookup"><span data-stu-id="39900-128">The project should compile without errors and run as a generic WPF application.</span></span>

### <a name="add-code"></a><span data-ttu-id="39900-129">Dodaj kod</span><span class="sxs-lookup"><span data-stu-id="39900-129">Add code</span></span>

1. <span data-ttu-id="39900-130">W **Eksplorator rozwiązań**Zmień nazwę pliku źródłowego **window1. XAML** na **L2XDBForm. XAML**.</span><span class="sxs-lookup"><span data-stu-id="39900-130">In **Solution Explorer**, rename the source file **Window1.xaml** to **L2XDBForm.xaml**.</span></span>

   <span data-ttu-id="39900-131">Window1.xaml.cs pliku źródłowego zależnego jest automatycznie zmieniana na L2XDBForm.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="39900-131">The dependent source file Window1.xaml.cs is automatically renamed to L2XDBForm.xaml.cs.</span></span>

1. <span data-ttu-id="39900-132">Zamień kod źródłowy znaleziony w pliku **L2XDBForm. XAML** na [kod źródłowy kod źródłowy L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="39900-132">Replace the source code found in the file **L2XDBForm.xaml** with the [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="39900-133">Użyj widoku źródła XAML do pracy z tym plikiem.</span><span class="sxs-lookup"><span data-stu-id="39900-133">Use the XAML source view to work with this file.</span></span>

1. <span data-ttu-id="39900-134">Podobnie zastąp źródło w **L2XDBForm.XAML.cs** z [kodem źródłowym L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="39900-134">Similarly, replace the source in **L2XDBForm.xaml.cs** with the [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

1. <span data-ttu-id="39900-135">W pliku **App. XAML**Zamień wszystkie wystąpienia ciągu **window1. XAML** na **L2XDBForm. XAML**.</span><span class="sxs-lookup"><span data-stu-id="39900-135">In the file **App.xaml**, replace all occurrences of the string **Window1.xaml** with **L2XDBForm.xaml**.</span></span>

1. <span data-ttu-id="39900-136">Skompiluj rozwiązanie, naciskając klawisz **Ctrl** +**SHIFT** +**B**.</span><span class="sxs-lookup"><span data-stu-id="39900-136">Build the solution by pressing **Ctrl**+**Shift**+**B**.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="39900-137">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="39900-137">Run the app</span></span>

<span data-ttu-id="39900-138">Aplikacja elementu LinqToXmlDataBinding — umożliwia użytkownikowi wyświetlanie listy książek przechowywanych jako osadzony element XML i manipulowanie nimi.</span><span class="sxs-lookup"><span data-stu-id="39900-138">The LinqToXmlDataBinding app enables the user to view and manipulate a list of books that's stored as an embedded XML element.</span></span> <span data-ttu-id="39900-139">Uruchom aplikację, naciskając klawisz **F5** (Rozpocznij debugowanie) lub **Ctrl**+**F5** (Rozpocznij bez debugowania).</span><span class="sxs-lookup"><span data-stu-id="39900-139">Run the app by pressing **F5** (Start Debugging) or **Ctrl**+**F5** (Start Without Debugging).</span></span>

<span data-ttu-id="39900-140">Zostanie wyświetlone okno programu z tytułem **powiązania danych WPF przy użyciu LINQ to XML** .</span><span class="sxs-lookup"><span data-stu-id="39900-140">A program window with the title **WPF Data Binding using LINQ to XML** appears.</span></span>

<span data-ttu-id="39900-141">W górnej części interfejsu użytkownika jest wyświetlany nieprzetworzony **kod XML** , który reprezentuje listę książek.</span><span class="sxs-lookup"><span data-stu-id="39900-141">The top section of the UI displays the raw **XML** that represents the book list.</span></span> <span data-ttu-id="39900-142">Jest ona wyświetlana przy użyciu kontrolki <xref:System.Windows.Controls.TextBlock> WPF, która nie umożliwia interakcji za pośrednictwem myszy lub klawiatury.</span><span class="sxs-lookup"><span data-stu-id="39900-142">It is displayed using a WPF <xref:System.Windows.Controls.TextBlock> control, which does not enable interaction through the mouse or keyboard.</span></span>

<span data-ttu-id="39900-143">Druga sekcja pionowa z etykietą **lista książek**zawiera książki jako listę uporządkowaną jako zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="39900-143">The second vertical section, labeled **Book List**, displays the books as a plain text ordered list.</span></span> <span data-ttu-id="39900-144">Używa kontrolki <xref:System.Windows.Controls.ListBox>, która umożliwia wybór za pośrednictwem myszy lub klawiatury.</span><span class="sxs-lookup"><span data-stu-id="39900-144">It uses a <xref:System.Windows.Controls.ListBox> control that enables selection though the mouse or keyboard.</span></span>

### <a name="add-and-delete-books"></a><span data-ttu-id="39900-145">Dodawanie i usuwanie książek</span><span class="sxs-lookup"><span data-stu-id="39900-145">Add and delete books</span></span>

<span data-ttu-id="39900-146">Aby dodać nową książkę do listy, wprowadź wartości w polu **Identyfikator** i **wartość** <xref:System.Windows.Controls.TextBox> kontrolki w ostatniej sekcji, **Dodaj nową książkę**, a następnie wybierz pozycję **Dodaj książkę**.</span><span class="sxs-lookup"><span data-stu-id="39900-146">To add a new book to the list, enter values into the **ID** and **Value** <xref:System.Windows.Controls.TextBox> controls in the last section, **Add New Book**, and then select **Add Book**.</span></span> <span data-ttu-id="39900-147">Książka jest dołączana do listy w listach książki i XML.</span><span class="sxs-lookup"><span data-stu-id="39900-147">The book is appended to the list in both the book and XML listings.</span></span> <span data-ttu-id="39900-148">Ten program nie weryfikuje wartości wejściowych.</span><span class="sxs-lookup"><span data-stu-id="39900-148">This program does not validate input values.</span></span>

<span data-ttu-id="39900-149">Aby usunąć istniejącą książkę z listy, wybierz ją w sekcji **lista książek** , a następnie wybierz pozycję **Usuń wybraną książkę**.</span><span class="sxs-lookup"><span data-stu-id="39900-149">To delete an existing book from the list, select it in the **Book List** section, and then select **Remove Selected Book**.</span></span> <span data-ttu-id="39900-150">Wpis książki jest usuwany z list książek i nieprzetworzonych źródeł XML.</span><span class="sxs-lookup"><span data-stu-id="39900-150">The book entry is removed from both the book and the raw XML source listings.</span></span>

### <a name="edit-a-book-entry"></a><span data-ttu-id="39900-151">Edytuj wpis książki</span><span class="sxs-lookup"><span data-stu-id="39900-151">Edit a book entry</span></span>

1. <span data-ttu-id="39900-152">Wybierz wpis książki w drugiej sekcji **listy książek** .</span><span class="sxs-lookup"><span data-stu-id="39900-152">Select the book entry in the second **Book List** section.</span></span>

   <span data-ttu-id="39900-153">Bieżące wartości są wyświetlane w sekcji **Edytuj wybraną książkę** .</span><span class="sxs-lookup"><span data-stu-id="39900-153">Its current values are displayed in the **Edit Selected Book** section.</span></span>

1. <span data-ttu-id="39900-154">Edytuj wartości przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="39900-154">Edit the values using the keyboard.</span></span> <span data-ttu-id="39900-155">Gdy tylko formant <xref:System.Windows.Controls.TextBox> utraci fokus, zmiany są automatycznie propagowane do listy źródłowej XML i książki.</span><span class="sxs-lookup"><span data-stu-id="39900-155">As soon as either <xref:System.Windows.Controls.TextBox> control loses focus, changes are automatically propagated to the XML source and book listings.</span></span>
