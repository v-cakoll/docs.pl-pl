---
title: 'Samouczek: Definiowanie kontraktu usługi Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228396"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="f611f-102">Samouczek: Definiowanie kontraktu usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f611f-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="f611f-103">W tym samouczku opisano pierwszy pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f611f-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="f611f-104">Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f611f-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="f611f-105">Podczas tworzenia usługi WCF, pierwsze zadanie jest definiowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f611f-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="f611f-106">Kontrakt usługi określa, jakie operacje obsługuje usługi.</span><span class="sxs-lookup"><span data-stu-id="f611f-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="f611f-107">Operacja można traktować jako metoda usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f611f-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="f611f-108">Tworzenie kontraktów usług, definiując wizualizacji C# lub interfejs Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="f611f-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="f611f-109">Interfejs ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="f611f-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="f611f-110">Każda metoda w interfejsie odpowiada określonej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f611f-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="f611f-111">Dla każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f611f-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="f611f-112">Dla każdej operacji/metody, należy najpierw zastosować <xref:System.ServiceModel.OperationContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f611f-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="f611f-113">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f611f-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="f611f-114">Tworzenie **biblioteki usługi WCF** projektu.</span><span class="sxs-lookup"><span data-stu-id="f611f-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="f611f-115">Zdefiniuj interfejs kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f611f-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="f611f-116">Utwórz projekt biblioteki usługi WCF i definiowanie interfejsu kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="f611f-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="f611f-117">Otwórz program Visual Studio jako administrator.</span><span class="sxs-lookup"><span data-stu-id="f611f-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="f611f-118">Aby to zrobić, wybierz program Visual Studio w **Start** menu, a następnie wybierz pozycję **więcej** > **Uruchom jako administrator** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="f611f-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="f611f-119">Tworzenie **biblioteki usługi WCF** projektu.</span><span class="sxs-lookup"><span data-stu-id="f611f-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="f611f-120">Z **pliku** menu, wybierz opcję **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f611f-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="f611f-121">W **nowy projekt** okna dialogowego po lewej stronie rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **WCF** kategorii.</span><span class="sxs-lookup"><span data-stu-id="f611f-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="f611f-122">Visual Studio Wyświetla listy szablonów projektu w w górnej części okna.</span><span class="sxs-lookup"><span data-stu-id="f611f-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="f611f-123">Wybierz **biblioteki usługi WCF**.</span><span class="sxs-lookup"><span data-stu-id="f611f-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="f611f-124">Jeśli nie widzisz **WCF** kategorii szablonu projektu, użytkownik może być konieczne zainstalowanie **Windows Communication Foundation** składnika programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f611f-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="f611f-125">W **nowy projekt** okno dialogowe, wybierz opcję **Otwórz Instalator programu Visual Studio** link po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="f611f-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="f611f-126">Wybierz **poszczególne składniki** kartę, a następnie znajdź i zaznacz **Windows Communication Foundation** w obszarze **działań programistycznych** kategorii.</span><span class="sxs-lookup"><span data-stu-id="f611f-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="f611f-127">Wybierz **Modyfikuj** do rozpoczęcia instalacji tego składnika.</span><span class="sxs-lookup"><span data-stu-id="f611f-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="f611f-128">W dolnej części okna wprowadź *GettingStartedLib* dla **nazwa** i *GettingStarted* dla **Nazwa rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="f611f-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="f611f-129">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="f611f-129">Select **OK**.</span></span>

      <span data-ttu-id="f611f-130">Program Visual Studio tworzy projekt, który ma trzy pliki: *IService1.cs* (lub *IService1.vb* dla projektów języka Visual Basic), *Service1.cs* (lub *Service1.vb* dla projektów języka Visual Basic), a  *App.config*. Program Visual Studio definiuje te pliki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f611f-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="f611f-131">*IService1* plik zawiera definicję domyślną kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f611f-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="f611f-132">*Service1* plik zawiera domyślną implementację elementu kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f611f-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="f611f-133">*App.config* plik zawiera informacje o konfiguracji potrzebne do załadowania domyślnej usługi za pomocą narzędzia Host usługi WCF w usłudze Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f611f-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="f611f-134">Aby uzyskać więcej informacji o narzędziu Host usługi WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f611f-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="f611f-135">Po zainstalowaniu programu Visual Studio z ustawieniami środowiska dewelopera języka Visual Basic, rozwiązanie może być ukryta.</span><span class="sxs-lookup"><span data-stu-id="f611f-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="f611f-136">Jeśli jest to możliwe, wybierz opcję **opcje** z **narzędzia** menu, następnie wybierz pozycję **projekty i rozwiązania** > **ogólne** w **opcje** okna.</span><span class="sxs-lookup"><span data-stu-id="f611f-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="f611f-137">Wybierz **zawsze pokazuj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="f611f-137">Select **Always show solution**.</span></span> <span data-ttu-id="f611f-138">Ponadto upewnij się, że **Zapisz nowe projekty po utworzeniu** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f611f-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="f611f-139">Z **Eksploratora rozwiązań**, otwórz **IService1.cs** lub **IService1.vb** pliku i zastąp jego kod poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="f611f-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="f611f-140">Ten kontrakt definiuje kalkulatora online.</span><span class="sxs-lookup"><span data-stu-id="f611f-140">This contract defines an online calculator.</span></span> <span data-ttu-id="f611f-141">Zwróć uwagę `ICalculator` interfejs z oznaczeniem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu (uproszczone jako `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="f611f-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="f611f-142">Ten atrybut definiuje przestrzeni nazw, aby odróżnić nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f611f-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="f611f-143">Ten kod oznacza każda operacja Kalkulator, za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu (uproszczone jako `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="f611f-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f611f-144">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f611f-144">Next steps</span></span>

<span data-ttu-id="f611f-145">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f611f-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="f611f-146">Utwórz projekt biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f611f-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="f611f-147">Zdefiniuj interfejs kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f611f-147">Define a service contract interface.</span></span>

<span data-ttu-id="f611f-148">Przejdź do następnego samouczka, aby dowiedzieć się, jak: Implementowanie kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f611f-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f611f-149">Samouczek: Implementowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="f611f-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
