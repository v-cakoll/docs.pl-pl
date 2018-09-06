---
title: 'Instrukcje: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: 1b30da34f7c85cccd98b18cd32b81c83630989b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43725062"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="f6b00-102">Instrukcje: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f6b00-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>

<span data-ttu-id="f6b00-103">Czasami konieczne jest uzyskanie informacji z inną usługę przepływu pracy usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f6b00-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span> <span data-ttu-id="f6b00-104">W tym temacie przedstawiono sposób wywoływania jednej usługi przepływu pracy z innego.</span><span class="sxs-lookup"><span data-stu-id="f6b00-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="f6b00-105">W tym temacie utworzymy dwie usługi przepływu pracy; taki, który ma metodę cofającą ciągu wejściowego, a druga, która konwertuje ciąg wejściowy na wielkie litery, po wycofaniu ciąg, który korzysta z pierwszej usługi.</span><span class="sxs-lookup"><span data-stu-id="f6b00-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>

### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="f6b00-106">Tworzenie usługi przepływu pracy system</span><span class="sxs-lookup"><span data-stu-id="f6b00-106">To create the Reverser workflow service</span></span>

1.  <span data-ttu-id="f6b00-107">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6b00-107">Open Visual Studio.</span></span>

2.  <span data-ttu-id="f6b00-108">Wybierz **pliku** > **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-108">Select **File** > **New Project**.</span></span> <span data-ttu-id="f6b00-109">W obszarze **przepływu pracy** w węźle **zainstalowane szablony** okienku wybierz **aplikacja usługi przepływu pracy WCF**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="f6b00-110">Nazwij rozwiązanie `NestedServices` a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-110">Name the solution `NestedServices` and then click **OK**.</span></span>

3.  <span data-ttu-id="f6b00-111">W obszarze **serwerów**, upewnij się, że **użycia lokalnego serwera sieci Web usług IIS** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f6b00-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="f6b00-112">Kliknij przycisk **Utwórz katalog wirtualny**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="f6b00-113">Kliknij przycisk **OK** w oknie dialogowym stwierdzające katalog wirtualny został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="f6b00-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>

4.  <span data-ttu-id="f6b00-114">W Eksploratorze rozwiązań, zmienianie nazwy Service1.xamlx do `StringReverserService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="f6b00-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>

5.  <span data-ttu-id="f6b00-115">Na **właściwości projektu** strony dla nowego projektu, kliknij przycisk **Web** kartę. Ustaw **Akcja uruchamiania** do **konkretnej strony**i wybierz StringReverserService.xamlx jako stronę aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="f6b00-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>

6.  <span data-ttu-id="f6b00-116">Otwórz StringReverserService.xamlx w projektancie, a następnie usuń istniejącą `ReceiveRequest` i `SendReply` działań, a następnie przeciągnij `ReceiveAndSendReply` działanie do istniejącego działania sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f6b00-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>

    1.  <span data-ttu-id="f6b00-117">Ustaw **OperationName** do ReverseString.</span><span class="sxs-lookup"><span data-stu-id="f6b00-117">Set the **OperationName** to ReverseString.</span></span>

    2.  <span data-ttu-id="f6b00-118">Ustaw **ServiceContractName** do IReverseString.</span><span class="sxs-lookup"><span data-stu-id="f6b00-118">Set the **ServiceContractName** to IReverseString.</span></span>

    3.  <span data-ttu-id="f6b00-119">Wybierz **CanCreateInstance** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="f6b00-119">Select the **CanCreateInstance** check box.</span></span>

7.  <span data-ttu-id="f6b00-120">Wybierz **SequentialService** działania, a następnie kliknij **zmienne** karty u dołu projektanta.</span><span class="sxs-lookup"><span data-stu-id="f6b00-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="f6b00-121">Utwórz dwa nowe zmienne o nazwach StringToReverse i ReversedStringToReturn typu String.</span><span class="sxs-lookup"><span data-stu-id="f6b00-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>

8.  <span data-ttu-id="f6b00-122">Kliknij przycisk **Definiuj** łącze w **Receive** działania.</span><span class="sxs-lookup"><span data-stu-id="f6b00-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="f6b00-123">Kliknij przycisk **parametry**i utworzyć parametr o nazwie InputString typu ciąg, który przypisuje StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="f6b00-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>

9. <span data-ttu-id="f6b00-124">Kliknij przycisk **Definiuj** łącze w **SendReplyToReceive** działania.</span><span class="sxs-lookup"><span data-stu-id="f6b00-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="f6b00-125">Kliknij przycisk **parametry**i utworzyć parametr o nazwie ReversedString typu String, przypisany do ReversedStringToReturn.</span><span class="sxs-lookup"><span data-stu-id="f6b00-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>

10. <span data-ttu-id="f6b00-126">Aby zaimplementować logikę dla usługi, Utwórz nową klasę w projekcie o nazwie StringLibrary.</span><span class="sxs-lookup"><span data-stu-id="f6b00-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="f6b00-127">Zastąp definicję klasy z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f6b00-127">Replace the class definition with the following code.</span></span>

    ```
    public class StringLibrary
        {
            public static String ReverseString(string StringToReverse)
            {
                char[] charArray = StringToReverse.ToCharArray();
                Array.Reverse(charArray);
                return new String(charArray);
            }
        }
    ```

11. <span data-ttu-id="f6b00-128">Aby wywołać metodę ReverseString w danych wejściowych, przeciągnij **InvokeMethod** działania z przybornika odstęp między **Receive** i **SendReply** działań.</span><span class="sxs-lookup"><span data-stu-id="f6b00-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="f6b00-129">Ustaw właściwości działania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f6b00-129">Set the properties of the activity as follows:</span></span>

    1.  <span data-ttu-id="f6b00-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="f6b00-130">**MethodName**: ReverseString</span></span>

    2.  <span data-ttu-id="f6b00-131">**Wynik**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="f6b00-131">**Result**: ReversedStringToReturn</span></span>

    3.  <span data-ttu-id="f6b00-132">**Parametry**: Tworzenie nowego parametru za pomocą **kierunek** z In, **typu** ciągu, a **wartość** z StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="f6b00-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>

    4.  <span data-ttu-id="f6b00-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="f6b00-133">**TargetType**: NestedServices.StringLibrary</span></span>

12. <span data-ttu-id="f6b00-134">Testować usługę, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="f6b00-134">Test the service by pressing F5.</span></span> <span data-ttu-id="f6b00-135">W kliencie testowym WCF, która jest wyświetlana kliknij dwukrotnie metodę ReverseString().</span><span class="sxs-lookup"><span data-stu-id="f6b00-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="f6b00-136">W okienku żądanie wprowadź `Sample` dla wartości parametru InputString.</span><span class="sxs-lookup"><span data-stu-id="f6b00-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="f6b00-137">Kliknij przycisk **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-137">Click **Invoke**.</span></span> <span data-ttu-id="f6b00-138">Usługa powinna zwrócić "elpmaS".</span><span class="sxs-lookup"><span data-stu-id="f6b00-138">The service should return "elpmaS".</span></span>

### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="f6b00-139">Tworzenie usługi przepływu pracy UpperCaser</span><span class="sxs-lookup"><span data-stu-id="f6b00-139">To create the UpperCaser workflow service</span></span>

1.  <span data-ttu-id="f6b00-140">Kliknij prawym przyciskiem myszy projekt NestedServices, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-140">Right-click the NestedServices project and select **Add** > **New Item**.</span></span> <span data-ttu-id="f6b00-141">W **przepływu pracy** węzeł **usługi przepływu pracy WCF**i nadaj nazwę nowej usługi `UpperCaserService`.</span><span class="sxs-lookup"><span data-stu-id="f6b00-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="f6b00-142">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-142">Click **Add**.</span></span> <span data-ttu-id="f6b00-143">Powinno to dodanie nowej usługi przepływu pracy o nazwie UpperCaserService.xamlx do projektu.</span><span class="sxs-lookup"><span data-stu-id="f6b00-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>

2.  <span data-ttu-id="f6b00-144">Otwórz UpperCaserService.xamlx w projektancie, a następnie usuń istniejącą **ReceiveRequest** i `SendReply` działań, a następnie przeciągnij `ReceiveAndSendReply` działanie do istniejącego działania sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f6b00-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>

    1.  <span data-ttu-id="f6b00-145">Ustaw **OperationName** do UpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="f6b00-145">Set the **OperationName** to UpperCaseString.</span></span>

    2.  <span data-ttu-id="f6b00-146">Ustaw **ServiceContractName** do IUpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="f6b00-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>

    3.  <span data-ttu-id="f6b00-147">Wybierz **CanCreateInstance** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="f6b00-147">Select the **CanCreateInstance** check box.</span></span>

3.  <span data-ttu-id="f6b00-148">Wybierz działanie SequentialService, a następnie kliknij przycisk **zmienne** karty u dołu projektanta.</span><span class="sxs-lookup"><span data-stu-id="f6b00-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="f6b00-149">Utwórz trzy nowe zmienne o nazwach StringToUpper, StringToReverse i StringToReturn typu String.</span><span class="sxs-lookup"><span data-stu-id="f6b00-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>

4.  <span data-ttu-id="f6b00-150">Kliknij przycisk **Definiuj** łącze w **Receive** działania.</span><span class="sxs-lookup"><span data-stu-id="f6b00-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="f6b00-151">Kliknij przycisk **parametry**i utworzyć parametr o nazwie InputString typu ciąg, który przypisuje StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="f6b00-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>

5.  <span data-ttu-id="f6b00-152">Kliknij przycisk **Definiuj** łącze w **SendReplyToReceive** działania.</span><span class="sxs-lookup"><span data-stu-id="f6b00-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="f6b00-153">Kliknij przycisk **parametry**i utworzyć parametr o nazwie ModifiedString typu String, przypisany do StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="f6b00-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>

6.  <span data-ttu-id="f6b00-154">Aby zaimplementować logikę dla usługi, utworzenie nowej metody w klasie StringLibrary, używając następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="f6b00-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>

    ```
    public static String UpperCaseString(string StringToUpperCase)
    {
         return StringToUpperCase.ToUpper();

    }
    ```

7.  <span data-ttu-id="f6b00-155">Aby wywołać metodę UpperCaseString w danych wejściowych, przeciągnij **InvokeMethod** działania z przybornika odstęp między **Receive** i **SendReply** działań.</span><span class="sxs-lookup"><span data-stu-id="f6b00-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="f6b00-156">Ustaw właściwości działania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f6b00-156">Set the properties of the activity as follows:</span></span>

    1.  <span data-ttu-id="f6b00-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="f6b00-157">**MethodName**: UpperCaseString</span></span>

    2.  <span data-ttu-id="f6b00-158">**Wynik**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="f6b00-158">**Result**: StringToReverse</span></span>

    3.  <span data-ttu-id="f6b00-159">**Parametry**: Tworzenie nowego parametru za pomocą **kierunek** z In, **typu** ciągu, a **wartość** z StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="f6b00-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>

    4.  <span data-ttu-id="f6b00-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="f6b00-160">**TargetType**: NestedServices.StringLibrary</span></span>

8.  <span data-ttu-id="f6b00-161">Teraz Zadzwonimy pierwszej usługi zmodyfikowaną wersją tego ciągu.</span><span class="sxs-lookup"><span data-stu-id="f6b00-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="f6b00-162">Kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-162">Right-click the project and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="f6b00-163">Dodaj odwołanie do niej usługi http://localhost/NestedServices/StringReverserService.xamlx i skompiluj projekt, aby utworzyć niestandardowe działanie, aby uzyskać dostęp do pierwszego usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f6b00-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>

9. <span data-ttu-id="f6b00-164">Przeciągnij nowe działanie wystąpienia przepływu pracy, między **InvokeMethod** działania i **SendReplyToReceive** działań.</span><span class="sxs-lookup"><span data-stu-id="f6b00-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="f6b00-165">Przypisywanie zmiennej StringToReverse właściwością InputString nowe działanie i zmiennych StringToReturn właściwości StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="f6b00-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>

10. <span data-ttu-id="f6b00-166">Otwórz stronę właściwości dla projektu NestedServices i zmień **konkretnej strony** w **Web** kartę, aby UpperCaserService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="f6b00-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>

11. <span data-ttu-id="f6b00-167">Testować usługę, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="f6b00-167">Test the service by pressing F5.</span></span> <span data-ttu-id="f6b00-168">W kliencie testowym WCF, która jest wyświetlana kliknij dwukrotnie metodę ReverseString().</span><span class="sxs-lookup"><span data-stu-id="f6b00-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="f6b00-169">W okienku żądanie wprowadź `Sample` dla wartości parametru InputString.</span><span class="sxs-lookup"><span data-stu-id="f6b00-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="f6b00-170">Kliknij przycisk **wywołania**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-170">Click **Invoke**.</span></span> <span data-ttu-id="f6b00-171">Usługa powinna zwrócić "ELPMAS".</span><span class="sxs-lookup"><span data-stu-id="f6b00-171">The service should return "ELPMAS".</span></span>

### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="f6b00-172">Można utworzyć klienta do wywołania usługi</span><span class="sxs-lookup"><span data-stu-id="f6b00-172">To create a client to call the services</span></span>

1.  <span data-ttu-id="f6b00-173">Dodaj nowy projekt aplikacji konsoli, nazywane klienta do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f6b00-173">Add a new Console application project called Client to the solution.</span></span>

2.  <span data-ttu-id="f6b00-174">Kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz pozycję **Dodaj** > **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-174">Right-click the Client project and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="f6b00-175">W wyświetlonym oknie kliknij **odnajdź**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="f6b00-176">Wybierz StringReverserService.xamlx i wprowadzili ReverseService przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f6b00-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="f6b00-177">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f6b00-177">Click **OK**.</span></span>

3.  <span data-ttu-id="f6b00-178">Zastąp metodę Main w pliku Program.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f6b00-178">Replace the Main method in Program.cs with the following code.</span></span>

    ```
    static void Main(string[] args)
    {
        Console.Write("Input string to process:");
        String input = Console.ReadLine();
        var service = new ReverseService.ReverseStringClient();
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));
        Console.ReadKey();
    }
    ```