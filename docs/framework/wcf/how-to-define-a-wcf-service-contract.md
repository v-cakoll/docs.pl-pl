---
title: 'Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation'
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5e8abbf8c5f9b0696d90ccbee94c5d8f4dd8b1ec
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809228"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="63cda-102">Instrukcje: Definiowanie kontraktu usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="63cda-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="63cda-103">Jest to pierwszy sześciu zadania wymagane do tworzenia podstawowej aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="63cda-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="63cda-104">Omówienie sześciu wszystkich zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="63cda-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="63cda-105">Podczas tworzenia usługi WCF, pierwszym zadaniem jest definiowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="63cda-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="63cda-106">Kontrakt usługi określa, jakie operacje obsługuje usługi.</span><span class="sxs-lookup"><span data-stu-id="63cda-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="63cda-107">Operację można traktować jako metoda usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="63cda-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="63cda-108">Kontrakty są tworzone przez definiowanie interfejsu C++, C# lub Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="63cda-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="63cda-109">Każda metoda w interfejsie odpowiada określonej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="63cda-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="63cda-110">Każdego interfejsu należy zastosować <xref:System.ServiceModel.ServiceContractAttribute> zastosować dla niego i każdej operacji musi być <xref:System.ServiceModel.OperationContractAttribute> atrybut zastosowany do niego.</span><span class="sxs-lookup"><span data-stu-id="63cda-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="63cda-111">Jeśli metoda w interfejsie z atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybut nie ma <xref:System.ServiceModel.OperationContractAttribute> atrybutu, że metoda nie jest uwidaczniana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="63cda-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>  
  
 <span data-ttu-id="63cda-112">Kod używany w tym zadaniu podano w przykładzie poniżej procedury.</span><span class="sxs-lookup"><span data-stu-id="63cda-112">The code used for this task is provided in the example following the procedure.</span></span>  
  
### <a name="to-define-a-service-contract"></a><span data-ttu-id="63cda-113">Aby zdefiniować kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="63cda-113">To define a service contract</span></span>  
  
1.  <span data-ttu-id="63cda-114">Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako administrator, klikając prawym przyciskiem myszy program w **Start** menu i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="63cda-114">Open  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] as an administrator by right-clicking the program in the **Start** menu and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="63cda-115">Tworzenie projektu biblioteki usługi WCF, klikając **pliku** menu i wybierając **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="63cda-115">Create a WCF Service Library project by clicking the **File** menu and selecting **New**, **Project**.</span></span> <span data-ttu-id="63cda-116">W **nowy projekt** okna dialogowego, po lewej stronie okna dialogowego rozwiń **Visual C#** dla projektu C# lub **inne języki** , a następnie **Visual Basic** dla projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="63cda-116">In the **New Project** dialog, on the left-hand side of the dialog expand **Visual C#** for a C# project or **Other Languages** and then **Visual Basic** for a Visual Basic project.</span></span> <span data-ttu-id="63cda-117">W obszarze Język wybrany wybierz **WCF** i listę szablonów projektu będzie wyświetlana na w górnej części okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="63cda-117">Under the language selected select **WCF** and a list of project templates will be displayed on the center section of the dialog.</span></span> <span data-ttu-id="63cda-118">Wybierz **biblioteki usługi WCF**i wpisz `GettingStartedLib` w **nazwa** pole tekstowe i `GettingStarted` w **Nazwa rozwiązania** textbox w dolnej części okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="63cda-118">Select **WCF Service Library**, and type `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>  
  
3.  <span data-ttu-id="63cda-119">Visual Studio utworzy projekt, który zawiera pliki 3: IService1.cs (lub IService1.vb) Service1.cs (lub Service1.vb) i pliku App.config.  Plik IService1 zawiera kontrakt usługi domyślne.</span><span class="sxs-lookup"><span data-stu-id="63cda-119">Visual Studio will create the project which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config.  The IService1 file contains a default service contract.</span></span>  <span data-ttu-id="63cda-120">Plik Service1 zawiera domyślną implementację kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="63cda-120">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="63cda-121">Plik App.config zawiera konfiguracji potrzebne do załadowania domyślna usługa z hostem usługi WCF programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63cda-121">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="63cda-122">Aby uzyskać więcej informacji o narzędziu Host usługi WCF, zobacz [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="63cda-122">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>  
  
4.  <span data-ttu-id="63cda-123">Otwórz plik IService1.cs lub IService1.vb i Usuń kod w deklaracji przestrzeni nazw, pozostawiając deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="63cda-123">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration leaving the namespace declaration.</span></span> <span data-ttu-id="63cda-124">W obszarze nazw deklaracji Zdefiniuj nowy interfejs o nazwie `ICalculator` jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="63cda-124">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
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
  
    ```  
    ‘IService.vb  
    Imports System  
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
  
     <span data-ttu-id="63cda-125">Ten kontrakt definiuje Kalkulator online.</span><span class="sxs-lookup"><span data-stu-id="63cda-125">This contract defines an online calculator.</span></span> <span data-ttu-id="63cda-126">Powiadomienie `ICalculator` interfejs jest oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="63cda-126">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="63cda-127">Ten atrybut definiuje przestrzeni nazw, która służy do odróżniania nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="63cda-127">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="63cda-128">Każda operacja Kalkulator jest oznaczony atrybutem <xref:System.ServiceModel.OperationContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="63cda-128">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63cda-129">Adnotuj interfejsu, elementu członkowskiego lub klasy za pomocą atrybutów, można usunąć część "Atrybutu" z nazwy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="63cda-129">When using attributes to annotate an interface, member, or class, you can drop the "Attribute" part from the attribute name.</span></span> <span data-ttu-id="63cda-130">Dlatego <xref:System.ServiceModel.ServiceContractAttribute> staje się `[ServiceContract]` w języku C# lub `<ServiceContract>` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="63cda-130">So <xref:System.ServiceModel.ServiceContractAttribute> becomes `[ServiceContract]` in C#, or `<ServiceContract>` in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63cda-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63cda-131">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="63cda-132">Instrukcje: implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="63cda-132">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="63cda-133">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="63cda-133">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="63cda-134">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="63cda-134">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
