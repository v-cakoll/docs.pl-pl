---
title: "Za pomocą klasy z typu CodeActivity tworzenia działania przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9894926ba93461d332eaac248c71d20ea4e7d30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="ef3ab-102">Za pomocą klasy z typu CodeActivity tworzenia działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ef3ab-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>
<span data-ttu-id="ef3ab-103">Działania utworzone przez dziedziczenie z <xref:System.Activities.CodeActivity> można zaimplementować podstawowe zachowanie ważnych przez zastąpienie <xref:System.Activities.CodeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
## <a name="using-codeactivitycontext"></a><span data-ttu-id="ef3ab-104">Przy użyciu CodeActivityContext</span><span class="sxs-lookup"><span data-stu-id="ef3ab-104">Using CodeActivityContext</span></span>  
 <span data-ttu-id="ef3ab-105">Funkcje środowiska uruchomieniowego przepływu pracy są dostępne z poziomu <xref:System.Activities.CodeActivity.Execute%2A> metody przy użyciu elementów członkowskich `context` parametr typu <xref:System.Activities.CodeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="ef3ab-106">Funkcji dostępnych za pośrednictwem <xref:System.Activities.CodeActivityContext> są następujące:</span><span class="sxs-lookup"><span data-stu-id="ef3ab-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>  
  
-   <span data-ttu-id="ef3ab-107">Pobieranie i ustawianie wartości zmiennych i argumentów.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-107">Getting and setting the values of variables and arguments.</span></span>  
  
-   <span data-ttu-id="ef3ab-108">Funkcje niestandardowe śledzenia przy użyciu <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>  
  
-   <span data-ttu-id="ef3ab-109">Dostęp do właściwości wykonania działania za pomocą <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="ef3ab-110">Aby utworzyć niestandardowe działania, który dziedziczy z typu CodeActivity</span><span class="sxs-lookup"><span data-stu-id="ef3ab-110">To create a custom activity that inherits from CodeActivity</span></span>  
  
1.  <span data-ttu-id="ef3ab-111">Otwórz[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef3ab-111">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ef3ab-112">Wybierz **pliku**, **nowe**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="ef3ab-113">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="ef3ab-114">Wybierz **Biblioteka działań** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="ef3ab-115">Nazwa nowego projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-115">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="ef3ab-116">Kliknij prawym przyciskiem myszy Activity1.xaml w projekcie HelloActivity i wybierz **usunąć**.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="ef3ab-117">Kliknij prawym przyciskiem myszy projekt HelloActivity i wybierz **Dodaj** , a następnie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="ef3ab-118">Nazwa nowej klasy HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-118">Name the new class HelloActivity.cs.</span></span>  
  
5.  <span data-ttu-id="ef3ab-119">W pliku HelloActivity.cs, Dodaj następujący `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  <span data-ttu-id="ef3ab-120">Upewnij się nowa klasa dziedziczy <xref:System.Activities.CodeActivity> przez dodanie klasy podstawowej deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  <span data-ttu-id="ef3ab-121">Dodawanie funkcji do klasy, dodając <xref:System.Activities.CodeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <span data-ttu-id="ef3ab-122">Użyj <xref:System.Activities.CodeActivityContext> Aby utworzyć rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ef3ab-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```
