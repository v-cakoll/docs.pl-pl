---
title: 'Przewodnik: Utrwalanie obiektu za pomocąC#'
ms.date: 04/26/2018
ms.openlocfilehash: 5e3a327ca0a257c45de361e0b3734e0b127f9869
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851044"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="e5d67-102">Przewodnik: utrwalanie obiektu przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="e5d67-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="e5d67-103">Możesz użyć serializacji, aby zachować dane obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobieranie ich przy następnym utworzeniu wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5d67-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="e5d67-104">W tym instruktażu utworzysz obiekt podstawowy `Loan` i zachowasz jego dane do pliku.</span><span class="sxs-lookup"><span data-stu-id="e5d67-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="e5d67-105">Następnie dane zostaną pobrane z pliku po ponownym utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5d67-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5d67-106">Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="e5d67-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="e5d67-107">Jeśli aplikacja musi utworzyć plik, aplikacja musi mieć `Create` uprawnienie do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="e5d67-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="e5d67-108">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="e5d67-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="e5d67-109">Jeśli plik już istnieje, aplikacja wymaga tylko `Write` uprawnień, ale jest to małe uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="e5d67-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="e5d67-110">Jeśli to możliwe, bezpieczniejsze jest tworzenie plików podczas wdrażania i udzielanie `Read` uprawnień tylko jednemu plikowi (zamiast tworzenia uprawnień dla folderu).</span><span class="sxs-lookup"><span data-stu-id="e5d67-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="e5d67-111">Ponadto bardziej bezpieczne jest zapisanie danych do folderów użytkowników niż folder główny lub folder Program Files.</span><span class="sxs-lookup"><span data-stu-id="e5d67-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5d67-112">Ten przykład zapisuje dane w pliku formatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="e5d67-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="e5d67-113">Tych formatów nie należy używać w przypadku poufnych danych, takich jak hasła lub informacje o kartach kredytowych.</span><span class="sxs-lookup"><span data-stu-id="e5d67-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5d67-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e5d67-114">Prerequisites</span></span>

- <span data-ttu-id="e5d67-115">Aby skompilować i uruchomić, zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="e5d67-115">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="e5d67-116">Zainstaluj swój ulubiony Edytor kodu, jeśli jeszcze tego nie zrobiono.</span><span class="sxs-lookup"><span data-stu-id="e5d67-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="e5d67-117">Musisz zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="e5d67-117">Need to install a code editor?</span></span> <span data-ttu-id="e5d67-118">Wypróbuj [program Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="e5d67-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="e5d67-119">Przykład wymaga C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="e5d67-119">The example requires C# 7.3.</span></span> <span data-ttu-id="e5d67-120">Zobacz [Wybieranie wersji C# językowej](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="e5d67-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span> 

<span data-ttu-id="e5d67-121">Przykładowy kod można przeanalizować w trybie online [w repozytorium usługi GitHub dla platformy .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="e5d67-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="e5d67-122">Tworzenie obiektu pożyczek</span><span class="sxs-lookup"><span data-stu-id="e5d67-122">Creating the loan object</span></span>

<span data-ttu-id="e5d67-123">Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacji konsolowej, która używa klasy:</span><span class="sxs-lookup"><span data-stu-id="e5d67-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="e5d67-124">Utwórz nową aplikację.</span><span class="sxs-lookup"><span data-stu-id="e5d67-124">Create a new application.</span></span> <span data-ttu-id="e5d67-125">Wpisz `dotnet new console -o serialization` , aby utworzyć nową aplikację konsolową w podkatalogu o `serialization`nazwie.</span><span class="sxs-lookup"><span data-stu-id="e5d67-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="e5d67-126">Otwórz aplikację w edytorze i Dodaj nową klasę o nazwie `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="e5d67-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="e5d67-127">Dodaj następujący kod do `Loan` klasy:</span><span class="sxs-lookup"><span data-stu-id="e5d67-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="e5d67-128">Należy również utworzyć aplikację, która używa `Loan` klasy.</span><span class="sxs-lookup"><span data-stu-id="e5d67-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="e5d67-129">Serializacja obiektu pożyczek</span><span class="sxs-lookup"><span data-stu-id="e5d67-129">Serialize the loan object</span></span>

1. <span data-ttu-id="e5d67-130">Otwórz `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="e5d67-130">Open `Program.cs`.</span></span> <span data-ttu-id="e5d67-131">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e5d67-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="e5d67-132">Dodaj program obsługi zdarzeń dla `PropertyChanged` zdarzenia, a kilka wierszy, aby `Loan` zmodyfikować obiekt i wyświetlić zmiany.</span><span class="sxs-lookup"><span data-stu-id="e5d67-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="e5d67-133">Można zobaczyć dodatki w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e5d67-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="e5d67-134">W tym momencie można uruchomić kod i wyświetlić bieżące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e5d67-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="e5d67-135">Aplikacja wielokrotnie uruchamiana zawsze zapisuje te same wartości.</span><span class="sxs-lookup"><span data-stu-id="e5d67-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="e5d67-136">Nowy obiekt pożyczek jest tworzony za każdym razem, gdy uruchamiasz program.</span><span class="sxs-lookup"><span data-stu-id="e5d67-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="e5d67-137">W świecie rzeczywistym stawki odsetek zmieniają się okresowo, ale nie zawsze, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e5d67-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="e5d67-138">Kod serializacji oznacza zachowywanie najnowszej stopy odsetek między wystąpieniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5d67-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="e5d67-139">W następnym kroku wystarczy dodać serializację do klasy pożyczek.</span><span class="sxs-lookup"><span data-stu-id="e5d67-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="e5d67-140">Utrwalanie obiektu przy użyciu serializacji</span><span class="sxs-lookup"><span data-stu-id="e5d67-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="e5d67-141">Aby zachować wartości dla klasy pożyczek, należy najpierw oznaczyć klasę `Serializable` atrybutem.</span><span class="sxs-lookup"><span data-stu-id="e5d67-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="e5d67-142">Dodaj następujący kod powyżej definicji klasy pożyczek:</span><span class="sxs-lookup"><span data-stu-id="e5d67-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="e5d67-143"><xref:System.SerializableAttribute> Informuje kompilator, że wszystko w klasie może być utrwalone w pliku.</span><span class="sxs-lookup"><span data-stu-id="e5d67-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="e5d67-144">`PropertyChanged` Ponieważ zdarzenie nie reprezentuje części grafu obiektów, która powinna być przechowywana, nie powinno być serializowane.</span><span class="sxs-lookup"><span data-stu-id="e5d67-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="e5d67-145">Dzięki temu można serializować wszystkie obiekty, które są dołączone do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e5d67-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="e5d67-146">Można dodać <xref:System.NonSerializedAttribute> do deklaracji pola `PropertyChanged` dla programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e5d67-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="e5d67-147">Począwszy od C# 7,3, można dołączyć atrybuty do pola zapasowego właściwości automatycznie zaimplementowane przy użyciu `field` wartości docelowej.</span><span class="sxs-lookup"><span data-stu-id="e5d67-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="e5d67-148">Poniższy kod dodaje `TimeLastLoaded` Właściwość i oznacza ją jako niemożliwy do serializacji:</span><span class="sxs-lookup"><span data-stu-id="e5d67-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="e5d67-149">Następnym krokiem jest dodanie kodu serializacji do aplikacji LoanApp.</span><span class="sxs-lookup"><span data-stu-id="e5d67-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="e5d67-150">Aby serializować klasę i zapisać ją w pliku, należy użyć <xref:System.IO> przestrzeni nazw i. <xref:System.Runtime.Serialization.Formatters.Binary></span><span class="sxs-lookup"><span data-stu-id="e5d67-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="e5d67-151">Aby uniknąć wpisywania w pełni kwalifikowanych nazw, można dodać odwołania do niezbędnych przestrzeni nazw, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e5d67-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="e5d67-152">Następnym krokiem jest dodanie kodu w celu deserializacji obiektu z pliku po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5d67-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="e5d67-153">Dodaj stałą do klasy dla nazwy pliku serializowanej danych, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e5d67-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="e5d67-154">Następnie Dodaj następujący kod po wierszu, który tworzy `TestLoan` obiekt:</span><span class="sxs-lookup"><span data-stu-id="e5d67-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="e5d67-155">Najpierw należy sprawdzić, czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="e5d67-155">You first must check that the file exists.</span></span> <span data-ttu-id="e5d67-156">Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasę, aby odczytać plik binarny <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i klasę, aby przetłumaczyć plik.</span><span class="sxs-lookup"><span data-stu-id="e5d67-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="e5d67-157">Należy również przekonwertować typ strumienia na typ obiektu pożyczki.</span><span class="sxs-lookup"><span data-stu-id="e5d67-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="e5d67-158">Następnie musisz dodać kod, aby serializować klasę do pliku.</span><span class="sxs-lookup"><span data-stu-id="e5d67-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="e5d67-159">Dodaj następujący kod po istniejącym kodzie w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="e5d67-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="e5d67-160">W tym momencie możesz ponownie skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="e5d67-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="e5d67-161">Przy pierwszym uruchomieniu należy zauważyć, że stawki odsetek zaczynają się od 7,5, a następnie zmieniają się na 7,1.</span><span class="sxs-lookup"><span data-stu-id="e5d67-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="e5d67-162">Zamknij aplikację, a następnie uruchom ją ponownie.</span><span class="sxs-lookup"><span data-stu-id="e5d67-162">Close the application and then run it again.</span></span> <span data-ttu-id="e5d67-163">Teraz aplikacja drukuje wiadomość, która odczytała zapisany plik, a oprocentowanie to 7,1 nawet przed kodem, który go zmieni.</span><span class="sxs-lookup"><span data-stu-id="e5d67-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5d67-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5d67-164">See also</span></span>

- [<span data-ttu-id="e5d67-165">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="e5d67-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="e5d67-166">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e5d67-166">C# Programming Guide</span></span>](../..//index.md)
