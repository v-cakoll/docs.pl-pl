---
title: 'Samouczek: Definiowanie umowy serwisowej programu Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184094"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="5cb21-102">Samouczek: Definiowanie umowy serwisowej programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5cb21-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="5cb21-103">W tym samouczku opisano pierwsze z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5cb21-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="5cb21-104">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5cb21-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="5cb21-105">Podczas tworzenia usługi WCF, pierwszym zadaniem jest zdefiniowanie umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="5cb21-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="5cb21-106">Umowa serwisowa określa, jakie operacje obsługuje usługa.</span><span class="sxs-lookup"><span data-stu-id="5cb21-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="5cb21-107">Operację można traktować jako metodę usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5cb21-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="5cb21-108">Umowy serwisowe można utworzyć, definiując interfejs języka C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5cb21-108">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="5cb21-109">Interfejs ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="5cb21-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="5cb21-110">Każda metoda w interfejsie odpowiada określonej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5cb21-110">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="5cb21-111">Dla każdego interfejsu należy <xref:System.ServiceModel.ServiceContractAttribute> zastosować atrybut.</span><span class="sxs-lookup"><span data-stu-id="5cb21-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="5cb21-112">Dla każdej operacji/metody należy <xref:System.ServiceModel.OperationContractAttribute> zastosować atrybut.</span><span class="sxs-lookup"><span data-stu-id="5cb21-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="5cb21-113">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5cb21-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5cb21-114">Utwórz projekt **biblioteki usług WCF.**</span><span class="sxs-lookup"><span data-stu-id="5cb21-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="5cb21-115">Zdefiniuj interfejs umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="5cb21-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="5cb21-116">Tworzenie projektu biblioteki usług WCF i definiowanie interfejsu umowy serwisowej</span><span class="sxs-lookup"><span data-stu-id="5cb21-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="5cb21-117">Otwórz program Visual Studio jako administrator.</span><span class="sxs-lookup"><span data-stu-id="5cb21-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="5cb21-118">Aby to zrobić, wybierz program Visual Studio w menu **Start,** a następnie wybierz polecenie **Więcej** > **uruchom jako administrator** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5cb21-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="5cb21-119">Utwórz projekt **biblioteki usług WCF.**</span><span class="sxs-lookup"><span data-stu-id="5cb21-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="5cb21-120">Z menu **Plik** wybierz polecenie **Nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="5cb21-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="5cb21-121">W oknie dialogowym **Nowy projekt** po lewej stronie rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie wybierz kategorię **WCF.**</span><span class="sxs-lookup"><span data-stu-id="5cb21-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="5cb21-122">Visual Studio wyświetla listę szablonów projektów w środkowej sekcji okna.</span><span class="sxs-lookup"><span data-stu-id="5cb21-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="5cb21-123">Wybierz **bibliotekę usług WCF**.</span><span class="sxs-lookup"><span data-stu-id="5cb21-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="5cb21-124">Jeśli nie widzisz kategorii szablonu projektu **WCF,** może być konieczne zainstalowanie składnika **Programu Windows Communication Foundation** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5cb21-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="5cb21-125">W oknie dialogowym **Nowy projekt** wybierz łącze **Otwórz instalatora programu Visual Studio** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="5cb21-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="5cb21-126">Wybierz kartę **Poszczególne składniki,** a następnie znajdź i wybierz **pozycję Windows Communication Foundation** w kategorii Działania **deweloperów.**</span><span class="sxs-lookup"><span data-stu-id="5cb21-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="5cb21-127">Wybierz **pozycję Modyfikuj,** aby rozpocząć instalację składnika.</span><span class="sxs-lookup"><span data-stu-id="5cb21-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="5cb21-128">W dolnej części okna wprowadź *WprowadzenieStartedLib* dla **nazwy** i *GettingStarted* dla **nazwy rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="5cb21-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="5cb21-129">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5cb21-129">Select **OK**.</span></span>

      <span data-ttu-id="5cb21-130">Visual Studio tworzy projekt, który ma trzy pliki: *IService1.cs* (lub *IService1.vb* dla projektu języka Visual Basic), *Service1.cs* (lub *Service1.vb* dla projektu Visual Basic) i *App.config*. Program Visual Studio definiuje te pliki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5cb21-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="5cb21-131">Plik *IService1* zawiera domyślną definicję umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="5cb21-131">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="5cb21-132">Plik *Service1* zawiera domyślną implementację umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="5cb21-132">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="5cb21-133">Plik *App.config* zawiera informacje o konfiguracji potrzebne do załadowania domyślnej usługi za pomocą narzędzia Host usługi WCF programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5cb21-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="5cb21-134">Aby uzyskać więcej informacji na temat narzędzia Host usług WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5cb21-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="5cb21-135">Jeśli program Visual Studio został zainstalowany z ustawieniami środowiska dewelopera języka Visual Basic, rozwiązanie może być ukryte.</span><span class="sxs-lookup"><span data-stu-id="5cb21-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="5cb21-136">W takim przypadku wybierz **opcję Opcje** z menu **Narzędzia,** a następnie w oknie **Opcje** wybierz pozycję Projekty **i rozwiązania** > **ogólne.**</span><span class="sxs-lookup"><span data-stu-id="5cb21-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="5cb21-137">Wybierz **opcję Zawsze pokazuj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="5cb21-137">Select **Always show solution**.</span></span> <span data-ttu-id="5cb21-138">Sprawdź też, czy **opcja Zapisz nowe projekty po utworzeniu** jest zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="5cb21-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="5cb21-139">W **Eksploratorze rozwiązań**otwórz **plik IService1.cs** lub **IService1.vb** i zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5cb21-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="5cb21-140">Niniejsza umowa definiuje kalkulator online.</span><span class="sxs-lookup"><span data-stu-id="5cb21-140">This contract defines an online calculator.</span></span> <span data-ttu-id="5cb21-141">Zwróć `ICalculator` uwagę, że <xref:System.ServiceModel.ServiceContractAttribute> interfejs jest oznaczony `ServiceContract`atrybutem (uproszczonym jako ).</span><span class="sxs-lookup"><span data-stu-id="5cb21-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="5cb21-142">Ten atrybut definiuje obszar nazw, aby odróżnić nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5cb21-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="5cb21-143">Kod oznacza każdą operację kalkulatora atrybutem <xref:System.ServiceModel.OperationContractAttribute> (uproszczonym jako `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="5cb21-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5cb21-144">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5cb21-144">Next steps</span></span>

<span data-ttu-id="5cb21-145">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5cb21-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5cb21-146">Utwórz projekt biblioteki usług WCF.</span><span class="sxs-lookup"><span data-stu-id="5cb21-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="5cb21-147">Zdefiniuj interfejs umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="5cb21-147">Define a service contract interface.</span></span>

<span data-ttu-id="5cb21-148">Przejdź do następnego samouczka, aby dowiedzieć się, jak zaimplementować umowę serwisową WCF.</span><span class="sxs-lookup"><span data-stu-id="5cb21-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cb21-149">Samouczek: Zaimplementowanie umowy serwisowej WCF</span><span class="sxs-lookup"><span data-stu-id="5cb21-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
