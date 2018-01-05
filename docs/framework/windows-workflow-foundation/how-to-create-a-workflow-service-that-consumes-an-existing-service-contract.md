---
title: "Porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a754875dc3f7968086f4f92044205b8ebceb01e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="9eb44-102">Porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="9eb44-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="9eb44-103">Funkcje lepszą integrację usług sieci web i przepływów pracy w formularzu tworzenia pierwszej kontraktu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9eb44-103"> features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="9eb44-104">Narzędzie do projektowania przepływu pracy pierwszy kontraktu pozwala na projektowanie najpierw kontraktu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9eb44-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="9eb44-105">Narzędzie następnie automatycznie generuje szablon czynności w przyborniku operacji w umowie.</span><span class="sxs-lookup"><span data-stu-id="9eb44-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9eb44-106">Ten temat zawiera wskazówki krok po kroku dotyczące tworzenia usługi przepływu pracy pierwszy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9eb44-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9eb44-107">Programowanie usługi przepływu pracy pierwszy kontraktu, zobacz [kontraktu pierwszego tworzenia usługi przepływu pracy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="9eb44-107"> contract-first workflow service development, see [Contract First Workflow Service Development](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="9eb44-108">Tworzenie projektu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9eb44-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="9eb44-109">W [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], wybierz pozycję **pliku**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-109">In [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], select **File**, **New Project**.</span></span> <span data-ttu-id="9eb44-110">Wybierz **WCF** węźle **C#** w węźle **szablony** drzewa, a następnie wybierz **aplikacji usługi przepływu pracy WCF** szablonu.</span><span class="sxs-lookup"><span data-stu-id="9eb44-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="9eb44-111">Nazwa nowego projektu `ContractFirst` i kliknij przycisk **Ok**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="9eb44-112">Tworzenie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="9eb44-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="9eb44-113">Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** .</span><span class="sxs-lookup"><span data-stu-id="9eb44-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="9eb44-114">Wybierz **kod** węźle po lewej stronie oraz **klasy** szablonu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="9eb44-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="9eb44-115">Nazwa nowej klasy `IBookService` i kliknij przycisk **Ok**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="9eb44-116">W górnej części okna kodu, który pojawia się, Dodaj instrukcję Using `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="9eb44-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="9eb44-117">Zmień definicję klasy próbki do następujących definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9eb44-117">Change the sample class definition to the following interface definition.</span></span>  
  
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
  
4.  <span data-ttu-id="9eb44-118">Tworzenie projektu przez naciśnięcie przycisku **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="9eb44-119">Importowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="9eb44-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="9eb44-120">Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **kontraktu usługi Import**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="9eb44-121">W obszarze  **\<bieżącego projektu >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="9eb44-122">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="9eb44-123">Zostanie otwarte okno dialogowe informujący, że operacja zakończyła się pomyślnie, a wygenerowanego działania będzie wyświetlana w przyborniku po utworzeniu projektu.</span><span class="sxs-lookup"><span data-stu-id="9eb44-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="9eb44-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="9eb44-125">Tworzenie projektu przez naciśnięcie przycisku **Ctrl + Shift + B**, dzięki czemu importowanych działania zostanie wyświetlony w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="9eb44-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="9eb44-126">W **Eksploratora rozwiązań**, otwórz Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="9eb44-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="9eb44-127">Usługi przepływu pracy będą wyświetlane w projektancie.</span><span class="sxs-lookup"><span data-stu-id="9eb44-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="9eb44-128">Wybierz **sekwencji** działania.</span><span class="sxs-lookup"><span data-stu-id="9eb44-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="9eb44-129">Kliknij w oknie właściwości **...**</span><span class="sxs-lookup"><span data-stu-id="9eb44-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="9eb44-130">przycisk **ImplementedContract** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9eb44-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="9eb44-131">W **edytora kolekcji typu** okno zostanie wyświetlone, kliknij przycisk **typu** listy rozwijanej i wybierz **Przeglądaj w poszukiwaniu typów...**</span><span class="sxs-lookup"><span data-stu-id="9eb44-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="9eb44-132">wpis.</span><span class="sxs-lookup"><span data-stu-id="9eb44-132">entry.</span></span> <span data-ttu-id="9eb44-133">W **Przeglądaj i wybierz .net typ** okna dialogowego, w obszarze  **\<bieżącego projektu >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="9eb44-134">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-134">Click **OK**.</span></span> <span data-ttu-id="9eb44-135">W **edytora kolekcji typu** okna dialogowego, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9eb44-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="9eb44-136">Wybierz i Usuń **ReceiveRequest** i **SendResponse** działań.</span><span class="sxs-lookup"><span data-stu-id="9eb44-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="9eb44-137">Przeciągnij z przybornika, **Buy_ReceiveAndSendReply** i **Checkout_Receive** działania na **usługa Sekwencyjna** działania.</span><span class="sxs-lookup"><span data-stu-id="9eb44-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
