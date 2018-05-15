---
title: Kolejność przetwarzania za pomocą zasad
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: 15e274a7a513a3208e3a54575dc354310743b731
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="cc96d-102">Kolejność przetwarzania za pomocą zasad</span><span class="sxs-lookup"><span data-stu-id="cc96d-102">Order Processing with Policy</span></span>
<span data-ttu-id="cc96d-103">Przykładowe kolejność przetwarzania zasad przedstawiono niektóre najważniejsze funkcje wprowadzone w systemie [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="cc96d-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="cc96d-104">Nowy aparat reguł WF są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="cc96d-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="cc96d-105">Obsługa dotyczące przeciążania operatorów.</span><span class="sxs-lookup"><span data-stu-id="cc96d-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="cc96d-106">Obsługa `new` operatora, dzięki czemu użytkownicy mogą tworzyć nowe obiekty i tablice z reguł WF.</span><span class="sxs-lookup"><span data-stu-id="cc96d-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="cc96d-107">Obsługa metody rozszerzenia, aby interfejs w wywoływanie metod rozszerzeń z reguł WF użytkownika zgodny z styl kodowania C#.</span><span class="sxs-lookup"><span data-stu-id="cc96d-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc96d-108">W tym przykładzie wymaga, aby [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] jest zainstalowany, aby skompilować i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="cc96d-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="cc96d-109"> jest wymagany do otwierania plików projektu i rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cc96d-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="cc96d-110">W przykładzie pokazano `OrderProcessingPolicy` projektu w jest wprowadzana zamówienie klienta, składający się z Lista numerowana dostępne elementy i kod pocztowy.</span><span class="sxs-lookup"><span data-stu-id="cc96d-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="cc96d-111">Kolejność jest przetworzone pomyślnie, jeśli obie pozycje są prawidłowe; w przeciwnym razie zasady tworzy obiekty błąd, wykorzystując przeciążone `+` operatora, a także metodę rozszerzenie wstępnie zdefiniowanych informują użytkownika o błędach.</span><span class="sxs-lookup"><span data-stu-id="cc96d-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc96d-112">Aby uzyskać więcej informacji na temat metody rozszerzenia, zobacz [C# w wersji 3.0 specyfikacji](http://go.microsoft.com/fwlink/?LinkId=95402).</span><span class="sxs-lookup"><span data-stu-id="cc96d-112">For more information about extension methods, see [C# Version 3.0 Specification](http://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="cc96d-113">Próbka składa się z następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="cc96d-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="cc96d-114">`OrderErrorLibrary` Jest biblioteki klas, który definiuje `OrderError` i `OrderErrorCollection` klasy.</span><span class="sxs-lookup"><span data-stu-id="cc96d-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="cc96d-115">`OrderError` Jest tworzone wystąpienie, gdy wprowadzono nieprawidłowe dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="cc96d-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="cc96d-116">Biblioteka zawiera także metodę rozszerzenia o `OrderErrorCollection` klasy, która wyświetla `ErrorText` właściwości na wszystkich `OrderError` obiekty w `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="cc96d-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="cc96d-117">`OrderProcessingPolicy` Projekt jest aplikacją konsoli WF, która definiuje jedną `PolicyFromFile` działania.</span><span class="sxs-lookup"><span data-stu-id="cc96d-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="cc96d-118">Działanie ma następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="cc96d-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="cc96d-119">Ta reguła sprawdza, czy liczba elementów od 1 do 6 włącznie.</span><span class="sxs-lookup"><span data-stu-id="cc96d-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="cc96d-120">Jeśli numer jest prawidłowego zakresu, reguła nie zadziała (inne niż drukowanie do konsoli).</span><span class="sxs-lookup"><span data-stu-id="cc96d-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="cc96d-121">Jeśli numer nie jest od 1 do 6, `invalidItemNum` zasada wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cc96d-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="cc96d-122">Tworzy nowy `OrderError` obiektu, przekazanie jej numer wprowadzony i ustawia `ErrorText` i `CustomerName` właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="cc96d-123">Tworzy `invalidItemNumErrorCollection` obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="cc96d-124">Dodaje nowy `OrderError` wystąpienie do `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="cc96d-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="cc96d-125">Oznacza to obsługę `new` operatora, z którym można utworzyć wystąpienia obiektów wewnątrz reguły.</span><span class="sxs-lookup"><span data-stu-id="cc96d-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="cc96d-126">Ta reguła sprawdza, kod pocztowy zawiera 5 cyfr czy znajduje się w zakresie 99998 do 600.</span><span class="sxs-lookup"><span data-stu-id="cc96d-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="cc96d-127">Jeśli kod pocztowy jest prawidłowego zakresu, reguła nie zadziała (inne niż drukowanie do konsoli).</span><span class="sxs-lookup"><span data-stu-id="cc96d-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="cc96d-128">Jeśli długość kodu pocztowego jest mniejsza niż 5 lub kod pocztowy nie jest między 00600 i 99998, `invalidZip` zasada wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cc96d-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="cc96d-129">Tworzy `OrderError` obiektu, przekazanie jej wprowadzony, kod pocztowy i ustawia `ErrorText` i `CustomerName` właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="cc96d-130">Tworzy `invalidZipCodeErrorCollection` obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="cc96d-131">Dodaje nowy `OrderError` wystąpienie do nowo utworzonego `invalidZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="cc96d-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="cc96d-132">Ta zasada ponownie przedstawiono obsługę `new` operatora, który służy do tworzenia wystąpienia obiektów wewnątrz reguły.</span><span class="sxs-lookup"><span data-stu-id="cc96d-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="cc96d-133">Ta reguła sprawdza, czy wystąpiły błędy dodane przez poprzednie dwie reguły w dwóch `OrderErrorCollection` obiektów `invalidItemNumErrorCollection` i `invalidIZipCodeErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="cc96d-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="cc96d-134">Jeśli wystąpiły błędy (albo `invalidItemNumErrorCollection` lub `invalidZipCodeErrorCollection` nie jest `null`), reguła wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cc96d-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="cc96d-135">Wywołuje przeciążone `+` operatora, aby skopiować zawartość `invalidItemNumErrorCollection` i `invalidZipCodeErrorCollection` do `invalidOrdersCollection``OrderErrorCollection` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cc96d-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="cc96d-136">Wywołania `PrintOrderErrors` — metoda rozszerzenia na `invalidOrdersCollection` i wyprowadza `ErrorText` właściwości na wszystkich `orderError` obiekty w `invalidOrdersCollection`.</span><span class="sxs-lookup"><span data-stu-id="cc96d-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="cc96d-137">Przeciążony operator `+` na `OrderErrorCollection` jest zdefiniowany w `OrderErrorCollection` klasy w `OrderErrorLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="cc96d-138">Trwa dwa `OrderErrorCollection` obiekty i łączy je do jednej `OrderErrorCollection` obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="cc96d-139">`PrintOrderErrors` — Metoda rozszerzenia jest też definiowany w `OrderErrorLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="cc96d-140">Metody rozszerzenia są nowe C# funkcję, która umożliwia programistom dodawanie nowych metod do publicznego kontraktu istniejącego typu CLR, bez konieczności pochodną klasy lub skompiluj ponownie oryginalnego typu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="cc96d-141">Po uruchomieniu próbki monit wprowadź nazwę, numer elementu zakupu i kod pocztowy.</span><span class="sxs-lookup"><span data-stu-id="cc96d-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="cc96d-142">Te informacje jest następnie weryfikowany przez reguły zdefiniowane w działaniu zasad.</span><span class="sxs-lookup"><span data-stu-id="cc96d-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="cc96d-143">Oto przykładowe dane wyjściowe z programu.</span><span class="sxs-lookup"><span data-stu-id="cc96d-143">The following is sample output from the program.</span></span>  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cc96d-144">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="cc96d-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cc96d-145">Otwórz plik projektu OrderProcessingPolicy.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc96d-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="cc96d-146">Istnieją dwa różne projekty w rozwiązaniu: `OrderErrorLibrary` i `OrderProcessingPolicy`.</span><span class="sxs-lookup"><span data-stu-id="cc96d-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="cc96d-147">`OrderProcessingPolicy` Projekt używa klasy i metody zdefiniowane w `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="cc96d-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="cc96d-148">Tworzenie wszystkich projektów.</span><span class="sxs-lookup"><span data-stu-id="cc96d-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="cc96d-149">Kliknij przycisk **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="cc96d-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc96d-150">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cc96d-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cc96d-151">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="cc96d-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cc96d-152">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cc96d-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc96d-153">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="cc96d-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`