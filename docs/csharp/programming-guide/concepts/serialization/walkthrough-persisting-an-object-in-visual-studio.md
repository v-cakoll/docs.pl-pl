---
title: 'Wskazówki: Przechowywanie obiektu przy użyciu języka C#'
ms.date: 04/26/2018
ms.openlocfilehash: 6c9719dc3aaf997ea144515a553f787450e54041
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956185"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="ad4d1-102">Wskazówki: przechowywanie obiektu przy użyciu języka C#</span><span class="sxs-lookup"><span data-stu-id="ad4d1-102">Walkthrough: persisting an object using C#</span></span> #

<span data-ttu-id="ad4d1-103">Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, które umożliwia przechowywanie wartości i pobrać je przy następnym uruchomieniu tworzenia wystąpienia obiektu klasy.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="ad4d1-104">W tym przewodniku spowoduje utworzenie podstawowego `Loan` obiekt i utrwala jego danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="ad4d1-105">Następnie zostanie pobrać dane z pliku podczas ponownego tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad4d1-106">W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="ad4d1-107">Jeśli aplikacja musi utworzyć plik, musi mieć aplikację `Create` uprawnienia do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="ad4d1-108">Uprawnienia są skonfigurowane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="ad4d1-109">Jeśli plik już istnieje, aplikacja musi tylko `Write` uprawnienia, mniejszym uprawnień.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="ad4d1-110">Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu).</span><span class="sxs-lookup"><span data-stu-id="ad4d1-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="ad4d1-111">Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż w folderze głównym lub folderze Program Files.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad4d1-112">W tym przykładzie przechowuje dane w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="ad4d1-113">Nie można używać tych formatów dla poufnych danych, takie jak hasła lub karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad4d1-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ad4d1-114">Prerequisites</span></span>

* <span data-ttu-id="ad4d1-115">Aby skompilować i uruchomić, należy zainstalować [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="ad4d1-115">To build and run, install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="ad4d1-116">Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="ad4d1-117">Należy zainstalować Edytor kodu?</span><span class="sxs-lookup"><span data-stu-id="ad4d1-117">Need to install a code editor?</span></span> <span data-ttu-id="ad4d1-118">Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="ad4d1-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

<span data-ttu-id="ad4d1-119">Można sprawdzić w trybie online przykładowym kodzie [w repozytorium GitHub przykłady .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span><span class="sxs-lookup"><span data-stu-id="ad4d1-119">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="ad4d1-120">Tworzenie obiektu pożyczki</span><span class="sxs-lookup"><span data-stu-id="ad4d1-120">Creating the loan object</span></span>

<span data-ttu-id="ad4d1-121">Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacja konsolowa, która używa klasy:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-121">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="ad4d1-122">Utwórz nową aplikację.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-122">Create a new application.</span></span> <span data-ttu-id="ad4d1-123">Typ `dotnet new console -o serialization` Aby utworzyć nową aplikację konsoli w podkatalogu o nazwie `serialization`.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-123">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="ad4d1-124">Otwórz aplikację w edytorze i Dodaj nową klasę o nazwie `Loan.cs`.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-124">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="ad4d1-125">Dodaj następujący kod do Twojej `Loan` klasy:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-125">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="ad4d1-126">Należy także utworzyć aplikację, która używa `Loan` klasy.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-126">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="ad4d1-127">Serializacji obiektu pożyczki</span><span class="sxs-lookup"><span data-stu-id="ad4d1-127">Serialize the loan object</span></span>

1. <span data-ttu-id="ad4d1-128">Otwórz `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-128">Open `Program.cs`.</span></span> <span data-ttu-id="ad4d1-129">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-129">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="ad4d1-130">Dodaj program obsługi zdarzeń dla `PropertyChanged` zdarzeń i kilka wierszy do modyfikowania `Loan` obiektu i wyświetlić zmiany.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-130">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="ad4d1-131">Można wyświetlić dodatków w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-131">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="ad4d1-132">W tym momencie możesz uruchomić kod i wyświetlone bieżące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-132">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="ad4d1-133">Uruchomienie takiej aplikacji wielokrotnie zawsze zapisuje te same wartości.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-133">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="ad4d1-134">Za każdym razem, gdy program zostanie uruchomiony, jest tworzony nowy obiekt pożyczki.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-134">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="ad4d1-135">W świecie rzeczywistym odsetek zmienić okresowo, ale niekoniecznie każdym uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-135">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="ad4d1-136">Kod serializacji oznacza, że Zachowaj najnowsze stopie procentowej między wystąpieniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-136">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="ad4d1-137">W następnym kroku zostanie czy właśnie tę dodając serializacji do klasy pożyczki.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-137">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="ad4d1-138">Za pomocą serializacji, aby utrwalić obiektu</span><span class="sxs-lookup"><span data-stu-id="ad4d1-138">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="ad4d1-139">Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę atrybutem `Serializable` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-139">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="ad4d1-140">Dodaj następujący kod nad pożyczki definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-140">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="ad4d1-141"><xref:System.SerializableAttribute> Informuje kompilator, że wszystkie elementy w klasie mógł być trwały do pliku.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-141">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="ad4d1-142">Ponieważ `PropertyChanged` zdarzenia nie reprezentuje część wykres obiektu, który powinien być przechowywany, nie powinien podlegać serializacji.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-142">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="ad4d1-143">Dzięki temu będzie serializować wszystkie obiekty, które są dołączone do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-143">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="ad4d1-144">Możesz dodać <xref:System.NonSerializedAttribute> do zgłoszenia pola `PropertyChanged` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-144">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="ad4d1-145">Począwszy od 7.3 C#, możesz dołączyć atrybuty do pola zapasowy przy użyciu automatycznie implementowanych właściwości `field` wartość docelowa.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-145">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="ad4d1-146">Poniższy kod dodaje `TimeLastLoaded` właściwości i oznacza je jako nie można serializować:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-146">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="ad4d1-147">Następnym krokiem jest dodawanie do aplikacji LoanApp kodu serializacji.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-147">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="ad4d1-148">Aby można było serializować klasy i zapisze go w pliku, użyj <xref:System.IO> i <xref:System.Runtime.Serialization.Formatters.Binary> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-148">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="ad4d1-149">Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do niezbędne przestrzeni nazw, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-149">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="ad4d1-150">Następnym krokiem jest Dodaj kod, aby deserializować obiektu z pliku po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-150">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="ad4d1-151">Dodaj stałą do klasy dla danych serializacji. Nazwa pliku, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-151">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="ad4d1-152">Następnie dodaj następujący kod po wierszu, który tworzy `TestLoan` obiektu:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-152">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="ad4d1-153">Musisz najpierw sprawdzić, czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-153">You first must check that the file exists.</span></span> <span data-ttu-id="ad4d1-154">Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy odczytanie pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-154">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="ad4d1-155">Należy również konwertować z typu stream z typem obiektu pożyczki.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-155">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="ad4d1-156">Następnie należy dodać kodu do serializacji klasy w pliku.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-156">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="ad4d1-157">Dodaj następujący kod po istniejący kod w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="ad4d1-157">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="ad4d1-158">W tym momencie możesz ponownie skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-158">At this point, you can again build and run the application.</span></span> <span data-ttu-id="ad4d1-159">Podczas pierwszego uruchomienia, zwróć uwagę, że odsetek rozpoczyna się w wersji 7.5, a następnie zmienia 7.1.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-159">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="ad4d1-160">Zamknij aplikację i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-160">Close the application and then run it again.</span></span> <span data-ttu-id="ad4d1-161">Teraz aplikacja wyświetla komunikat, że ma odczytu zapisany plik, a stopie procentowej 7.1 nawet przed kod, który powoduje.</span><span class="sxs-lookup"><span data-stu-id="ad4d1-161">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad4d1-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad4d1-162">See also</span></span>

 [<span data-ttu-id="ad4d1-163">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="ad4d1-163">Serialization (C# )</span></span>](index.md)  
 [<span data-ttu-id="ad4d1-164">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ad4d1-164">C# Programming Guide</span></span>](../..//index.md)  
