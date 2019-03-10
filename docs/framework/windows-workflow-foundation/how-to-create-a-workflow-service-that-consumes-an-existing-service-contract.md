---
title: 'Instrukcje: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 57babf216821665613da053f972ff25488418b7d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705067"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="6ff04-102">Instrukcje: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="6ff04-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="6ff04-103">Funkcje lepszą integrację między usługami sieci web i przepływów pracy w formie Projektowanie przepływów pracy z wymogiem wcześniejszego zawarcia kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6ff04-103">features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="6ff04-104">Narzędzie tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu umożliwia projektowanie najpierw kontrakt w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6ff04-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="6ff04-105">Narzędzie następnie automatycznie generuje szablon działania w przyborniku dla operacji w kontrakcie.</span><span class="sxs-lookup"><span data-stu-id="6ff04-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ff04-106">Ten temat zawiera wskazówki krok po kroku dotyczące tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="6ff04-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="6ff04-107">Aby uzyskać więcej informacji na temat programowanie usługi przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu, zobacz [kontraktu pierwszy programowanie usługi przepływu pracy](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="6ff04-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="6ff04-108">Tworzenie projektu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6ff04-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="6ff04-109">W programie Visual Studio, wybierz **pliku**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="6ff04-110">Wybierz **WCF** węźle **C#** w węźle **szablony** drzewa, a następnie wybierz **aplikacja usługi przepływu pracy WCF** szablon.</span><span class="sxs-lookup"><span data-stu-id="6ff04-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="6ff04-111">Nazwa nowego projektu `ContractFirst` i kliknij przycisk **Ok**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="6ff04-112">Tworzenie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="6ff04-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="6ff04-113">Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** .</span><span class="sxs-lookup"><span data-stu-id="6ff04-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="6ff04-114">Wybierz **kodu** węzła po lewej stronie, a **klasy** szablonu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="6ff04-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="6ff04-115">Nadaj nowej klasie `IBookService` i kliknij przycisk **Ok**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="6ff04-116">W górnej części okna kodu, który pojawia się, Dodaj instrukcję Using do `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="6ff04-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="6ff04-117">Zmień definicję klasy przykładowe następująca definicja interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6ff04-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  <span data-ttu-id="6ff04-118">Skompiluj projekt, naciskając klawisz **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="6ff04-119">Trwa importowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="6ff04-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="6ff04-120">Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Importuj kontrakt usługi**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="6ff04-121">W obszarze  **\<bieżący projekt >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="6ff04-122">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="6ff04-123">Zostanie otwarte okno dialogowe alerty, operacja ukończona pomyślnie, a które wygenerowane działania zostaną wyświetlone w przyborniku, po skompilowaniu projektu.</span><span class="sxs-lookup"><span data-stu-id="6ff04-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="6ff04-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="6ff04-125">Skompiluj projekt, naciskając klawisz **Ctrl + Shift + B**, dzięki czemu importowanych działania będą wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="6ff04-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="6ff04-126">W **Eksploratora rozwiązań**, otwórz Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="6ff04-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="6ff04-127">W Projektancie pojawi się usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6ff04-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="6ff04-128">Wybierz **sekwencji** działania.</span><span class="sxs-lookup"><span data-stu-id="6ff04-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="6ff04-129">W oknie dialogowym właściwości kliknij **...**</span><span class="sxs-lookup"><span data-stu-id="6ff04-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="6ff04-130">znajdujący się w **ImplementedContract** właściwości.</span><span class="sxs-lookup"><span data-stu-id="6ff04-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="6ff04-131">W **Editor typu Kolekce** okna, które zostanie wyświetlone, kliknij przycisk **typu** listy rozwijanej i wybierz **vyhledat typy...**</span><span class="sxs-lookup"><span data-stu-id="6ff04-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="6ff04-132">wpis.</span><span class="sxs-lookup"><span data-stu-id="6ff04-132">entry.</span></span> <span data-ttu-id="6ff04-133">W **przeglądania i wybierz pozycję .net typu** okna dialogowego, w obszarze  **\<bieżący projekt >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="6ff04-134">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-134">Click **OK**.</span></span> <span data-ttu-id="6ff04-135">W **Editor typu Kolekce** okno dialogowe, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ff04-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="6ff04-136">Wybierz i Usuń **ReceiveRequest** i **SendResponse** działań.</span><span class="sxs-lookup"><span data-stu-id="6ff04-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="6ff04-137">Z przybornika przeciągnij **Buy_ReceiveAndSendReply** i **Checkout_Receive** działania na **usługa Sekwencyjna** działania.</span><span class="sxs-lookup"><span data-stu-id="6ff04-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
