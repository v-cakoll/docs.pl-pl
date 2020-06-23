---
title: 'Samouczek: Definiowanie kontraktu usługi Windows Communication Foundation'
description: Dowiedz się, jak zdefiniować kontrakt usługi w ramach serii artykułów, które ułatwiają rozpoczęcie tworzenia aplikacji WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246314"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="7b471-103">Samouczek: Definiowanie kontraktu usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7b471-103">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="7b471-104">W tym samouczku opisano pierwsze pięć zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7b471-104">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="7b471-105">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="7b471-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="7b471-106">Podczas tworzenia usługi WCF pierwsze zadanie polega na zdefiniowaniu kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="7b471-106">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="7b471-107">Kontrakt usługi określa operacje obsługiwane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="7b471-107">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="7b471-108">Operację można traktować jako metodę usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7b471-108">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="7b471-109">Kontrakty usługi można tworzyć, definiując interfejs C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7b471-109">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="7b471-110">Interfejs ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="7b471-110">An interface has the following characteristics:</span></span>

- <span data-ttu-id="7b471-111">Każda metoda w interfejsie odpowiada określonej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7b471-111">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="7b471-112">Dla każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="7b471-112">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="7b471-113">Dla każdej operacji/metody należy zastosować <xref:System.ServiceModel.OperationContractAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="7b471-113">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="7b471-114">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7b471-114">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="7b471-115">Utwórz projekt **biblioteki usługi WCF** .</span><span class="sxs-lookup"><span data-stu-id="7b471-115">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="7b471-116">Zdefiniuj interfejs kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="7b471-116">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="7b471-117">Utwórz projekt biblioteki usługi WCF i zdefiniuj interfejs kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="7b471-117">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="7b471-118">Otwórz program Visual Studio jako administrator.</span><span class="sxs-lookup"><span data-stu-id="7b471-118">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="7b471-119">W tym celu wybierz program Visual Studio w menu **Start** , a następnie wybierz polecenie **więcej**  >  **Uruchom jako administrator** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="7b471-119">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="7b471-120">Utwórz projekt **biblioteki usługi WCF** .</span><span class="sxs-lookup"><span data-stu-id="7b471-120">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="7b471-121">Z menu **plik** wybierz pozycję **Nowy**  >  **projekt**.</span><span class="sxs-lookup"><span data-stu-id="7b471-121">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="7b471-122">W oknie dialogowym **Nowy projekt** po lewej stronie rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie wybierz kategorię **WCF** .</span><span class="sxs-lookup"><span data-stu-id="7b471-122">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="7b471-123">Program Visual Studio Wyświetla listę szablonów projektu w środkowej sekcji okna.</span><span class="sxs-lookup"><span data-stu-id="7b471-123">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="7b471-124">Wybierz pozycję **Biblioteka usług WCF**.</span><span class="sxs-lookup"><span data-stu-id="7b471-124">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="7b471-125">Jeśli nie widzisz kategorii szablonu projektu **WCF** , może być konieczne zainstalowanie składnika **Windows Communication Foundation** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b471-125">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="7b471-126">W oknie dialogowym **Nowy projekt** wybierz łącze **Otwórz Instalator programu Visual Studio** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="7b471-126">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="7b471-127">Wybierz kartę **poszczególne składniki** , a następnie Znajdź i wybierz **Windows Communication Foundation** w kategorii **działania rozwojowe** .</span><span class="sxs-lookup"><span data-stu-id="7b471-127">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="7b471-128">Wybierz pozycję **Modyfikuj** , aby rozpocząć instalowanie składnika.</span><span class="sxs-lookup"><span data-stu-id="7b471-128">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="7b471-129">W dolnej części okna wprowadź *GettingStartedLib* dla **nazwy** i *GettingStarted* **nazwy rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="7b471-129">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="7b471-130">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7b471-130">Select **OK**.</span></span>

      <span data-ttu-id="7b471-131">Program Visual Studio tworzy projekt, który ma trzy pliki: *IService1.cs* (lub *IService1. vb* dla projektu Visual Basic), *Service1.cs* (lub *Service1. vb* dla projektu Visual Basic) i *App.config*. Program Visual Studio definiuje te pliki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7b471-131">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="7b471-132">Plik *IService1* zawiera definicję domyślną kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="7b471-132">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="7b471-133">Plik *Service1* zawiera domyślną implementację kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="7b471-133">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="7b471-134">Plik *App.config* zawiera informacje o konfiguracji, które są konieczne do załadowania usługi domyślnej za pomocą narzędzia hosta usługi WCF programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b471-134">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="7b471-135">Aby uzyskać więcej informacji na temat narzędzia hosta usługi WCF, zobacz [host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7b471-135">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="7b471-136">Jeśli zainstalowano program Visual Studio z Visual Basic ustawieniach środowiska deweloperskiego, rozwiązanie może być ukryte.</span><span class="sxs-lookup"><span data-stu-id="7b471-136">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="7b471-137">W takim przypadku wybierz pozycję **Opcje** z menu **Narzędzia** , a następnie wybierz pozycję **projekty i rozwiązania**  >  **Ogólne** w oknie **Opcje** .</span><span class="sxs-lookup"><span data-stu-id="7b471-137">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="7b471-138">Wybierz pozycję **Zawsze pokazuj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="7b471-138">Select **Always show solution**.</span></span> <span data-ttu-id="7b471-139">Sprawdź również, czy wybrano opcję **Zapisz nowe projekty po utworzeniu** .</span><span class="sxs-lookup"><span data-stu-id="7b471-139">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="7b471-140">W **Eksplorator rozwiązań**otwórz plik **IService1.cs** lub **IService1. vb** i Zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7b471-140">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     <span data-ttu-id="7b471-141">Ten kontrakt definiuje Kalkulator online.</span><span class="sxs-lookup"><span data-stu-id="7b471-141">This contract defines an online calculator.</span></span> <span data-ttu-id="7b471-142">Zauważ, że `ICalculator` interfejs jest oznaczony <xref:System.ServiceModel.ServiceContractAttribute> atrybutem (uproszczony jako `ServiceContract` ).</span><span class="sxs-lookup"><span data-stu-id="7b471-142">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="7b471-143">Ten atrybut definiuje przestrzeń nazw, aby odróżnić nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7b471-143">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="7b471-144">Kod oznacza każdą operację kalkulatora z <xref:System.ServiceModel.OperationContractAttribute> atrybutem (uproszczony jako `OperationContract` ).</span><span class="sxs-lookup"><span data-stu-id="7b471-144">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7b471-145">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7b471-145">Next steps</span></span>

<span data-ttu-id="7b471-146">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7b471-146">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="7b471-147">Utwórz projekt biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7b471-147">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="7b471-148">Zdefiniuj interfejs kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="7b471-148">Define a service contract interface.</span></span>

<span data-ttu-id="7b471-149">Przejdź do następnego samouczka, aby dowiedzieć się, jak zaimplementować kontrakt usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7b471-149">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7b471-150">Samouczek: Implementowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="7b471-150">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
