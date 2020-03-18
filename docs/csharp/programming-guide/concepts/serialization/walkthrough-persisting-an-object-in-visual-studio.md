---
title: 'Instruktaż: Utrwalanie obiektu przy użyciu C #'
ms.date: 04/26/2018
ms.openlocfilehash: 85c5d1b711180eda5734d5860d996242c6bc89d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167573"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="f751c-102">Instruktaż: utrwalanie obiektu przy użyciu C\#</span><span class="sxs-lookup"><span data-stu-id="f751c-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="f751c-103">Serializacji można użyć do utrwalenia danych obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobieranie ich przy następnym wystąpieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f751c-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="f751c-104">W tym instruktażu `Loan` utworzysz obiekt podstawowy i utrwalisz jego dane do pliku.</span><span class="sxs-lookup"><span data-stu-id="f751c-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="f751c-105">Dane zostaną pobrane z pliku podczas ponownego tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f751c-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f751c-106">W tym przykładzie tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f751c-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="f751c-107">Jeśli aplikacja musi utworzyć plik, ta `Create` aplikacja musi mieć uprawnienia do folderu.</span><span class="sxs-lookup"><span data-stu-id="f751c-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="f751c-108">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="f751c-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="f751c-109">Jeśli plik już istnieje, aplikacja `Write` wymaga tylko uprawnień, mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="f751c-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="f751c-110">Jeśli to możliwe, bezpieczniej jest utworzyć plik podczas `Read` wdrażania i przyznać uprawnienia tylko jednemu plikowi (zamiast utwórz uprawnienia dla folderu).</span><span class="sxs-lookup"><span data-stu-id="f751c-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="f751c-111">Ponadto bezpieczniej jest zapisywać dane w folderach użytkowników niż w folderze głównym lub folderze Pliki programów.</span><span class="sxs-lookup"><span data-stu-id="f751c-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f751c-112">W tym przykładzie przechowuje dane w pliku w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="f751c-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="f751c-113">Formaty te nie powinny być używane w odniesieniu do poufnych danych, takich jak hasła lub informacje o karcie kredytowej.</span><span class="sxs-lookup"><span data-stu-id="f751c-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f751c-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f751c-114">Prerequisites</span></span>

- <span data-ttu-id="f751c-115">Aby utworzyć i uruchomić, zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="f751c-115">To build and run, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

- <span data-ttu-id="f751c-116">Zainstaluj swój ulubiony edytor kodu, jeśli jeszcze tego nie zrobiłeś.</span><span class="sxs-lookup"><span data-stu-id="f751c-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="f751c-117">Chcesz zainstalować edytor kodów?</span><span class="sxs-lookup"><span data-stu-id="f751c-117">Need to install a code editor?</span></span> <span data-ttu-id="f751c-118">[Wypróbuj program Visual Studio!](https://visualstudio.com/downloads)</span><span class="sxs-lookup"><span data-stu-id="f751c-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="f751c-119">Przykład wymaga Języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f751c-119">The example requires C# 7.3.</span></span> <span data-ttu-id="f751c-120">Zobacz [Wybieranie wersji językowej języka Języka C#](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="f751c-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span>

<span data-ttu-id="f751c-121">Przykładowy kod można sprawdzić w trybie online [w repozytorium github .NET .](https://github.com/dotnet/samples/tree/master/csharp/serialization)</span><span class="sxs-lookup"><span data-stu-id="f751c-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="f751c-122">Tworzenie obiektu pożyczki</span><span class="sxs-lookup"><span data-stu-id="f751c-122">Creating the loan object</span></span>

<span data-ttu-id="f751c-123">Pierwszym krokiem jest `Loan` utworzenie klasy i aplikacji konsoli, która używa klasy:</span><span class="sxs-lookup"><span data-stu-id="f751c-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="f751c-124">Utwórz nową aplikację.</span><span class="sxs-lookup"><span data-stu-id="f751c-124">Create a new application.</span></span> <span data-ttu-id="f751c-125">Wpisz, `dotnet new console -o serialization` aby utworzyć nową aplikację `serialization`konsoli w podkatalogu o nazwie .</span><span class="sxs-lookup"><span data-stu-id="f751c-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="f751c-126">Otwórz aplikację w edytorze i dodaj `Loan.cs`nową klasę o nazwie .</span><span class="sxs-lookup"><span data-stu-id="f751c-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="f751c-127">Dodaj następujący kod `Loan` do swojej klasy:</span><span class="sxs-lookup"><span data-stu-id="f751c-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="f751c-128">Należy również utworzyć aplikację, która `Loan` używa klasy.</span><span class="sxs-lookup"><span data-stu-id="f751c-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="f751c-129">Serializacja obiektu pożyczki</span><span class="sxs-lookup"><span data-stu-id="f751c-129">Serialize the loan object</span></span>

1. <span data-ttu-id="f751c-130">Otwórz plik `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="f751c-130">Open `Program.cs`.</span></span> <span data-ttu-id="f751c-131">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f751c-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

<span data-ttu-id="f751c-132">Dodaj program obsługi `PropertyChanged` zdarzeń dla zdarzenia i `Loan` kilka wierszy, aby zmodyfikować obiekt i wyświetlić zmiany.</span><span class="sxs-lookup"><span data-stu-id="f751c-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="f751c-133">Możesz zobaczyć dodatki w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f751c-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

<span data-ttu-id="f751c-134">W tym momencie można uruchomić kod i zobaczyć bieżące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f751c-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="f751c-135">Uruchamianie tej aplikacji wielokrotnie zawsze zapisuje te same wartości.</span><span class="sxs-lookup"><span data-stu-id="f751c-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="f751c-136">Nowy obiekt Pożyczka jest tworzony przy każdym uruchomieniu programu.</span><span class="sxs-lookup"><span data-stu-id="f751c-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="f751c-137">W świecie rzeczywistym stopy procentowe zmieniają się okresowo, ale niekoniecznie za każdym razem, gdy aplikacja jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="f751c-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="f751c-138">Kod serializacji oznacza zachowanie najnowszej stopy procentowej między wystąpieniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f751c-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="f751c-139">W następnym kroku zrobisz tylko, że dodając serializacji do Pożyczki klasy.</span><span class="sxs-lookup"><span data-stu-id="f751c-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="f751c-140">Używanie serializacji do utrwalania obiektu</span><span class="sxs-lookup"><span data-stu-id="f751c-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="f751c-141">Aby utrwalić wartości dla Klasy Pożyczki, należy `Serializable` najpierw oznaczyć klasę atrybutem.</span><span class="sxs-lookup"><span data-stu-id="f751c-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="f751c-142">Dodaj następujący kod powyżej definicji klasy pożyczki:</span><span class="sxs-lookup"><span data-stu-id="f751c-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="f751c-143">Informuje <xref:System.SerializableAttribute> kompilator, że wszystko w klasie można utrwalić do pliku.</span><span class="sxs-lookup"><span data-stu-id="f751c-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="f751c-144">Ponieważ `PropertyChanged` zdarzenie nie reprezentuje część wykresu obiektu, które powinny być przechowywane, nie powinny być serializowane.</span><span class="sxs-lookup"><span data-stu-id="f751c-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="f751c-145">W ten sposób można serializować wszystkie obiekty, które są dołączone do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f751c-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="f751c-146">Można dodać <xref:System.NonSerializedAttribute> do deklaracji pola `PropertyChanged` dla programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f751c-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="f751c-147">Począwszy od Języka C# 7.3, można dołączyć atrybuty do pola `field` zapasowego właściwości auto implementowane przy użyciu wartości docelowej.</span><span class="sxs-lookup"><span data-stu-id="f751c-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="f751c-148">Poniższy kod dodaje `TimeLastLoaded` właściwość i oznacza ją jako nieserializowalną:</span><span class="sxs-lookup"><span data-stu-id="f751c-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="f751c-149">Następnym krokiem jest dodanie kodu serializacji do aplikacji LoanApp.</span><span class="sxs-lookup"><span data-stu-id="f751c-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="f751c-150">Aby serializować klasę i zapisać ją do pliku, <xref:System.IO> należy <xref:System.Runtime.Serialization.Formatters.Binary> użyć i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f751c-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="f751c-151">Aby uniknąć wpisywania w pełni kwalifikowanych nazw, można dodać odwołania do niezbędnych obszarów nazw, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f751c-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

<span data-ttu-id="f751c-152">Następnym krokiem jest dodanie kodu do deserializacji obiektu z pliku podczas tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f751c-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="f751c-153">Dodaj stałą do klasy dla nazwy pliku danych serializowanych, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f751c-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

<span data-ttu-id="f751c-154">Następnie dodaj następujący kod po wierszu, który tworzy `TestLoan` obiekt:</span><span class="sxs-lookup"><span data-stu-id="f751c-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

<span data-ttu-id="f751c-155">Najpierw należy sprawdzić, czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="f751c-155">You first must check that the file exists.</span></span> <span data-ttu-id="f751c-156">Jeśli istnieje, utwórz <xref:System.IO.Stream> klasę do odczytu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pliku binarnego i klasę, aby przetłumaczyć plik.</span><span class="sxs-lookup"><span data-stu-id="f751c-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="f751c-157">Należy również przekonwertować z typu strumienia do typu Pożyczka typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f751c-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="f751c-158">Następnie należy dodać kod do serializacji klasy do pliku.</span><span class="sxs-lookup"><span data-stu-id="f751c-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="f751c-159">Dodaj następujący kod po istniejącym `Main` kodzie w metodzie:</span><span class="sxs-lookup"><span data-stu-id="f751c-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

<span data-ttu-id="f751c-160">W tym momencie można ponownie utworzyć i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f751c-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="f751c-161">Po raz pierwszy działa, należy zauważyć, że stopy procentowe zaczynają się od 7,5, a następnie zmienia się na 7,1.</span><span class="sxs-lookup"><span data-stu-id="f751c-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="f751c-162">Zamknij aplikację, a następnie uruchom ją ponownie.</span><span class="sxs-lookup"><span data-stu-id="f751c-162">Close the application and then run it again.</span></span> <span data-ttu-id="f751c-163">Teraz aplikacja drukuje komunikat, że przeczytał zapisany plik, a stopa procentowa wynosi 7,1 jeszcze przed kodem, który go zmienia.</span><span class="sxs-lookup"><span data-stu-id="f751c-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="f751c-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f751c-164">See also</span></span>

- [<span data-ttu-id="f751c-165">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="f751c-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="f751c-166">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f751c-166">C# Programming Guide</span></span>](../..//index.md)
