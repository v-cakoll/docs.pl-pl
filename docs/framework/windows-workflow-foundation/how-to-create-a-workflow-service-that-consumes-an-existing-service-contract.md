---
title: 'Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 6d7fa8c9faa84efc84243387cd27aa264f6155eb
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989624"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="18baf-102">Instrukcje: Tworzenie usługi przepływu pracy wykorzystującej istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="18baf-102">How to: Create a workflow service that consumes an existing service contract</span></span>
<span data-ttu-id="18baf-103">.NET Framework 4,5 funkcje lepsza integracja między usługami sieci Web i przepływami pracy w formie tworzenia przepływu pracy w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="18baf-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="18baf-104">Narzędzie do tworzenia przepływu pracy pierwszego kontraktu umożliwia zaprojektowanie kontraktu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="18baf-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="18baf-105">Narzędzie automatycznie generuje szablon działania w przyborniku dla operacji w kontrakcie.</span><span class="sxs-lookup"><span data-stu-id="18baf-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18baf-106">Ten temat zawiera wskazówki krok po kroku dotyczące tworzenia usługi przepływu pracy pierwszego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="18baf-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="18baf-107">Aby uzyskać więcej informacji na temat tworzenia usługi przepływu pracy w pierwszej kolejności, zobacz [pierwsze programowanie usługi przepływu pracy w ramach kontraktu](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="18baf-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="18baf-108">Tworzenie projektu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="18baf-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="18baf-109">W programie Visual Studio wybierz pozycję **plik**, **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="18baf-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="18baf-110">Wybierz węzeł **WCF** w **C#** węźle drzewa **szablonów** , a następnie wybierz szablon **aplikacja usługi przepływu pracy WCF** .</span><span class="sxs-lookup"><span data-stu-id="18baf-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="18baf-111">Nazwij nowy projekt `ContractFirst` , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="18baf-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="18baf-112">Tworzenie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="18baf-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="18baf-113">Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **nowy element.** ...</span><span class="sxs-lookup"><span data-stu-id="18baf-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="18baf-114">Wybierz węzeł **kod** po lewej stronie i szablon **klasy** po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="18baf-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="18baf-115">Nazwij nową klasę `IBookService` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="18baf-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="18baf-116">W górnej części wyświetlonego okna kod Dodaj instrukcję using do `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="18baf-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="18baf-117">Zmień definicję klasy przykładowej na następującą definicję interfejsu.</span><span class="sxs-lookup"><span data-stu-id="18baf-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="18baf-118">Skompiluj projekt, naciskając **klawisze CTRL + SHIFT + B**.</span><span class="sxs-lookup"><span data-stu-id="18baf-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="18baf-119">Importowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="18baf-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="18baf-120">Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **Importuj kontrakt usługi**.</span><span class="sxs-lookup"><span data-stu-id="18baf-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="18baf-121">W obszarze  **\<bieżący projekt >** Otwórz wszystkie węzły podrzędne i wybierz pozycję **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="18baf-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="18baf-122">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="18baf-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="18baf-123">Zostanie otwarte okno dialogowe z alertem, że operacja została ukończona pomyślnie, a wygenerowane działania będą widoczne w przyborniku po skompilowaniu projektu.</span><span class="sxs-lookup"><span data-stu-id="18baf-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="18baf-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="18baf-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="18baf-125">Skompiluj projekt, naciskając **klawisze CTRL + SHIFT + B**, aby zaimportowane działania pojawiły się w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="18baf-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="18baf-126">W **Eksplorator rozwiązań**Otwórz Service1. xamlx.</span><span class="sxs-lookup"><span data-stu-id="18baf-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="18baf-127">Usługa przepływu pracy będzie wyświetlana w projektancie.</span><span class="sxs-lookup"><span data-stu-id="18baf-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="18baf-128">Wybierz działanie **sekwencji** .</span><span class="sxs-lookup"><span data-stu-id="18baf-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="18baf-129">W okno Właściwości kliknij przycisk. **.**</span><span class="sxs-lookup"><span data-stu-id="18baf-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="18baf-130">przycisk we właściwości **ImplementedContract** .</span><span class="sxs-lookup"><span data-stu-id="18baf-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="18baf-131">W wyświetlonym oknie **Edytor kolekcji typów** kliknij listę rozwijaną **Typ** , a następnie wybierz pozycję **Przeglądaj w poszukiwaniu typów...**</span><span class="sxs-lookup"><span data-stu-id="18baf-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="18baf-132">Autotekstu.</span><span class="sxs-lookup"><span data-stu-id="18baf-132">entry.</span></span> <span data-ttu-id="18baf-133">W oknie dialogowym **Przeglądaj i wybierz typ platformy .NET** w obszarze  **\<bieżący projekt >** Otwórz wszystkie węzły podrzędne i wybierz pozycję **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="18baf-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="18baf-134">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="18baf-134">Click **OK**.</span></span> <span data-ttu-id="18baf-135">W oknie dialogowym **Edytor kolekcji typów** kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="18baf-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="18baf-136">Wybierz i Usuń działania **ReceiveRequest** i **SendResponse** .</span><span class="sxs-lookup"><span data-stu-id="18baf-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="18baf-137">Z przybornika przeciągnij działanie **Buy_ReceiveAndSendReply** i **Checkout_Receive** do działania **sekwencyjnego usługi** .</span><span class="sxs-lookup"><span data-stu-id="18baf-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
