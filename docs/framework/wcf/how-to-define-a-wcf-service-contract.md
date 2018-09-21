---
title: 'Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537881"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="a4008-102">Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a4008-102">How to: Define a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="a4008-103">Jest to pierwszy z sześciu zadań podrzędnych, wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a4008-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a4008-104">Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="a4008-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

 <span data-ttu-id="a4008-105">Podczas tworzenia usługi WCF, pierwsze zadanie jest definiowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="a4008-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="a4008-106">Kontrakt usługi określa, jakie operacje obsługuje usługi.</span><span class="sxs-lookup"><span data-stu-id="a4008-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="a4008-107">Operacja można traktować jako metoda usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a4008-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="a4008-108">Kontrakty są tworzone przez definiowanie interfejsu C++, C# lub Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="a4008-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="a4008-109">Każda metoda w interfejsie odpowiada określonej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a4008-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="a4008-110">Każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> zastosowano i każdej operacji musi być <xref:System.ServiceModel.OperationContractAttribute> zastosowany do niego.</span><span class="sxs-lookup"><span data-stu-id="a4008-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="a4008-111">Jeśli metoda w interfejsie z atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybut nie ma <xref:System.ServiceModel.OperationContractAttribute> atrybutu, że metoda nie są udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="a4008-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>

 <span data-ttu-id="a4008-112">Kod używany dla tego zadania znajduje się w przykładzie zamieszczonym po procedurze.</span><span class="sxs-lookup"><span data-stu-id="a4008-112">The code used for this task is provided in the example following the procedure.</span></span>

## <a name="define-a-service-contract"></a><span data-ttu-id="a4008-113">Definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="a4008-113">Define a service contract</span></span>

1. <span data-ttu-id="a4008-114">Otwórz program Visual Studio jako administrator, klikając prawym przyciskiem myszy program w **Start** menu i wybierając polecenie **więcej** > **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="a4008-114">Open Visual Studio as an administrator by right-clicking the program in the **Start** menu and selecting **More** > **Run as administrator**.</span></span>

2. <span data-ttu-id="a4008-115">Utwórz projekt biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a4008-115">Create a WCF Service Library project.</span></span>

   1. <span data-ttu-id="a4008-116">Z **pliku** menu, wybierz opcję **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a4008-116">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="a4008-117">W **nowy projekt** okna dialogowego po lewej stronie rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **WCF** kategorii.</span><span class="sxs-lookup"><span data-stu-id="a4008-117">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="a4008-118">Listy szablonów projektu jest wyświetlany w w górnej części okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="a4008-118">A list of project templates is displayed in the center section of the dialog.</span></span> <span data-ttu-id="a4008-119">Wybierz **biblioteki usługi WCF**.</span><span class="sxs-lookup"><span data-stu-id="a4008-119">Select **WCF Service Library**.</span></span>

   3. <span data-ttu-id="a4008-120">Wprowadź `GettingStartedLib` w **nazwa** pole tekstowe i `GettingStarted` w **Nazwa rozwiązania** pole tekstowe w dolnej części okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="a4008-120">Enter `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a4008-121">Jeśli nie widzisz **WCF** kategorii szablonu projektu, użytkownik może być konieczne zainstalowanie **Windows Communication Foundation** składnika programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4008-121">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="a4008-122">W **nowy projekt** okna dialogowego kliknij łącze, które mówi **Otwórz Instalator programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a4008-122">In the **New Project** dialog box, click the link that says **Open Visual Studio Installer**.</span></span> <span data-ttu-id="a4008-123">Wybierz **poszczególne składniki** kartę, a następnie znajdź i zaznacz **Windows Communication Foundation** w obszarze **działań programistycznych** kategorii.</span><span class="sxs-lookup"><span data-stu-id="a4008-123">Select the **Individual Components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="a4008-124">Wybierz **Modyfikuj** do rozpoczęcia instalacji tego składnika.</span><span class="sxs-lookup"><span data-stu-id="a4008-124">Choose **Modify** to begin installing the component.</span></span>

   <span data-ttu-id="a4008-125">Program Visual Studio tworzy projekt, który zawiera pliki 3: IService1.cs (lub IService1.vb) Service1.cs (lub Service1.vb) i pliku App.config. Plik IService1 zawiera domyślny kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="a4008-125">Visual Studio creates the project, which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config. The IService1 file contains a default service contract.</span></span> <span data-ttu-id="a4008-126">Plik Service1 zawiera domyślną implementację kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="a4008-126">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="a4008-127">Plik App.config zawiera konfiguracji potrzebne do załadowania domyślnej usługi za pomocą programu Visual Studio Host usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a4008-127">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="a4008-128">Aby uzyskać więcej informacji o narzędziu Host usługi WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="a4008-128">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>

3. <span data-ttu-id="a4008-129">Otwórz plik IService1.cs lub IService1.vb i Usuń kod w deklaracji przestrzeni nazw, pozostawiając deklarację przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a4008-129">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration, leaving the namespace declaration.</span></span> <span data-ttu-id="a4008-130">W obszarze nazw deklaracji Zdefiniuj nowy interfejs o nazwie `ICalculator` jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a4008-130">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>

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

     <span data-ttu-id="a4008-131">Ten kontrakt definiuje kalkulatora online.</span><span class="sxs-lookup"><span data-stu-id="a4008-131">This contract defines an online calculator.</span></span> <span data-ttu-id="a4008-132">Zwróć uwagę `ICalculator` interfejs z oznaczeniem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a4008-132">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="a4008-133">Ten atrybut definiuje obszar nazw, który służy do odróżniania nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a4008-133">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="a4008-134">Każda operacja Kalkulator jest oznaczona za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a4008-134">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a4008-135">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a4008-135">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4008-136">Porady: Implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="a4008-136">How to: Implement a service contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a><span data-ttu-id="a4008-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4008-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="a4008-138">Instrukcje: implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="a4008-138">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="a4008-139">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a4008-139">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="a4008-140">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="a4008-140">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)