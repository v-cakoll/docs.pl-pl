---
title: 'Samouczek: Zdefiniuj kontrakt usługi Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928877"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="8758c-102">Samouczek: Zdefiniuj kontrakt usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8758c-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="8758c-103">W tym samouczku opisano pierwsze pięć zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8758c-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="8758c-104">Aby zapoznać się z omówieniem samouczków, [zobacz Samouczek: Rozpocznij pracę z aplikacjami](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="8758c-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="8758c-105">Podczas tworzenia usługi WCF pierwsze zadanie polega na zdefiniowaniu kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="8758c-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="8758c-106">Kontrakt usługi określa operacje obsługiwane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="8758c-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="8758c-107">Operację można traktować jako metodę usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8758c-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="8758c-108">Kontrakty usługi można tworzyć przez zdefiniowanie C# interfejsu wizualizacji lub Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="8758c-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="8758c-109">Interfejs ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="8758c-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="8758c-110">Każda metoda w interfejsie odpowiada określonej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="8758c-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="8758c-111">Dla każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="8758c-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="8758c-112">Dla każdej operacji/metody należy zastosować <xref:System.ServiceModel.OperationContractAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="8758c-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="8758c-113">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8758c-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8758c-114">Utwórz projekt **biblioteki usługi WCF** .</span><span class="sxs-lookup"><span data-stu-id="8758c-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="8758c-115">Zdefiniuj interfejs kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="8758c-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="8758c-116">Utwórz projekt biblioteki usługi WCF i zdefiniuj interfejs kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="8758c-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="8758c-117">Otwórz program Visual Studio jako administrator.</span><span class="sxs-lookup"><span data-stu-id="8758c-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="8758c-118">W tym celu wybierz program Visual Studio w menu **Start** , a następnie wybierz polecenie **więcej** > **Uruchom jako administrator** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="8758c-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="8758c-119">Utwórz projekt **biblioteki usługi WCF** .</span><span class="sxs-lookup"><span data-stu-id="8758c-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="8758c-120">Z **pliku** menu, wybierz opcję **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="8758c-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="8758c-121">W oknie dialogowym **Nowy projekt** po lewej stronie rozwiń pozycję  **C# Wizualizacja** lub **Visual Basic**, a następnie wybierz kategorię **WCF** .</span><span class="sxs-lookup"><span data-stu-id="8758c-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="8758c-122">Program Visual Studio Wyświetla listę szablonów projektu w środkowej sekcji okna.</span><span class="sxs-lookup"><span data-stu-id="8758c-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="8758c-123">Wybierz pozycję **Biblioteka usług WCF**.</span><span class="sxs-lookup"><span data-stu-id="8758c-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="8758c-124">Jeśli nie widzisz kategorii szablonu projektu **WCF** , może być konieczne zainstalowanie składnika **Windows Communication Foundation** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8758c-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="8758c-125">W oknie dialogowym **Nowy projekt** wybierz łącze **Otwórz Instalator programu Visual Studio** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="8758c-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="8758c-126">Wybierz kartę **poszczególne składniki** , a następnie Znajdź i wybierz **Windows Communication Foundation** w kategorii **działania rozwojowe** .</span><span class="sxs-lookup"><span data-stu-id="8758c-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="8758c-127">Wybierz pozycję **Modyfikuj** , aby rozpocząć instalowanie składnika.</span><span class="sxs-lookup"><span data-stu-id="8758c-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="8758c-128">W dolnej części okna wprowadź *GettingStartedLib* dla **nazwy** i *GettingStarted* **nazwy rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="8758c-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="8758c-129">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8758c-129">Select **OK**.</span></span>

      <span data-ttu-id="8758c-130">Program Visual Studio tworzy projekt, który ma trzy pliki: *IService1.cs* (lub *IService1. vb* dla projektu Visual Basic), *Service1.cs* (lub *Service1. vb* dla projektu Visual Basic) i *App. config*. Program Visual Studio definiuje te pliki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8758c-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="8758c-131">Plik *IService1* zawiera definicję domyślną kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="8758c-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="8758c-132">Plik *Service1* zawiera domyślną implementację kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="8758c-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="8758c-133">Plik *App. config* zawiera informacje o konfiguracji, które są konieczne do załadowania usługi domyślnej za pomocą narzędzia hosta usługi WCF programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8758c-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="8758c-134">Aby uzyskać więcej informacji na temat narzędzia hosta usługi WCF, zobacz [host usługi WCF (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8758c-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="8758c-135">Jeśli zainstalowano program Visual Studio z Visual Basic ustawieniach środowiska deweloperskiego, rozwiązanie może być ukryte.</span><span class="sxs-lookup"><span data-stu-id="8758c-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="8758c-136">W takim przypadku wybierz pozycję **Opcje** z menu **Narzędzia** , a następnie wybierz pozycję **projekty i rozwiązania** > **Ogólne** w oknie **Opcje** .</span><span class="sxs-lookup"><span data-stu-id="8758c-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="8758c-137">Wybierz pozycję **Zawsze pokazuj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="8758c-137">Select **Always show solution**.</span></span> <span data-ttu-id="8758c-138">Sprawdź również, czy wybrano opcję **Zapisz nowe projekty po utworzeniu** .</span><span class="sxs-lookup"><span data-stu-id="8758c-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="8758c-139">W **Eksplorator rozwiązań**otwórz plik **IService1.cs** lub **IService1. vb** i Zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="8758c-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="8758c-140">Ten kontrakt definiuje Kalkulator online.</span><span class="sxs-lookup"><span data-stu-id="8758c-140">This contract defines an online calculator.</span></span> <span data-ttu-id="8758c-141">Zauważ, `ICalculator` że interfejs jest oznaczony <xref:System.ServiceModel.ServiceContractAttribute> atrybutem (uproszczony `ServiceContract`jako).</span><span class="sxs-lookup"><span data-stu-id="8758c-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="8758c-142">Ten atrybut definiuje przestrzeń nazw, aby odróżnić nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8758c-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="8758c-143">Kod oznacza każdą operację kalkulatora z <xref:System.ServiceModel.OperationContractAttribute> atrybutem (uproszczony jako `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="8758c-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8758c-144">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8758c-144">Next steps</span></span>

<span data-ttu-id="8758c-145">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8758c-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8758c-146">Utwórz projekt biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8758c-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="8758c-147">Zdefiniuj interfejs kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="8758c-147">Define a service contract interface.</span></span>

<span data-ttu-id="8758c-148">Przejdź do następnego samouczka, aby dowiedzieć się, jak zaimplementować kontrakt usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8758c-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8758c-149">Samouczek: Implementowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="8758c-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
