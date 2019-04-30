---
title: Klasa COM — przykład - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: e36dfe1117cc724f5388e3486a81310f2326ab7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710137"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="3d0c5-102">Klasa COM — Przykład (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3d0c5-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="3d0c5-103">Oto przykład klasy, który może narazić jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="3d0c5-104">Po ten kod został umieszczony w pliku CS i dodane do projektu, ustawić **Zarejestruj dla współdziałania COM** właściwości **True**.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="3d0c5-105">Aby uzyskać więcej informacji, zobacz [jak: Zarejestruj składnik COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3d0c5-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="3d0c5-106">Udostępnianie obiektów Visual C# dla modelu COM wymaga zadeklarowania interfejsu klasy, interfejsu zdarzenia w razie potrzeby i samej klasy.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="3d0c5-107">Elementy członkowskie klasy muszą wykonać następujące czynności, które mają być widoczne dla modelu COM:</span><span class="sxs-lookup"><span data-stu-id="3d0c5-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="3d0c5-108">Klasy muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-108">The class must be public.</span></span>  
  
- <span data-ttu-id="3d0c5-109">Właściwości, metody i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="3d0c5-110">Właściwości i metody musi być zadeklarowana w klasie interfejs.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="3d0c5-111">Zdarzenia musi być zadeklarowany w zdarzeniu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="3d0c5-112">Inne publiczne elementy członkowskie klasy, które nie są zadeklarowane za pomocą tych interfejsów nie będą widoczne dla modelu COM, ale będą one widoczne dla innych obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="3d0c5-113">Aby udostępnić właściwości i metody dla modelu COM, należy je zadeklarować interfejsu klasy i oznacz je za pomocą `DispId` atrybutu i ich wdrażania w klasie.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="3d0c5-114">Kolejność, w której elementy członkowskie są zadeklarowane w interfejsie polega na kolejności, używany dla modelu COM vtable.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="3d0c5-115">Aby udostępnić zdarzenia z klasy, należy zadeklarować je w interfejsie zdarzeń i oznacz je za pomocą `DispId` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="3d0c5-116">Klasy nie powinny implementować ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="3d0c5-117">Klasa implementuje interfejs klasy; implementuje on więcej niż jeden interfejs, ale pierwszego wdrożenia będzie domyślny interfejs klasy.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="3d0c5-118">Implementuje metody i właściwości uwidaczniany w modelu COM w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="3d0c5-119">One musi być oznaczona jako publiczna i musi być zgodna z deklaracji interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="3d0c5-120">Ponadto należy zadeklarować zdarzenia wygenerowane przez klasę, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="3d0c5-121">One musi być oznaczona jako publiczna i musi być zgodna z deklaracji zdarzenia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3d0c5-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d0c5-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d0c5-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="3d0c5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d0c5-123">See also</span></span>

- [<span data-ttu-id="3d0c5-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3d0c5-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3d0c5-125">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="3d0c5-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
- [<span data-ttu-id="3d0c5-126">Strona kompilacji, Projektant projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="3d0c5-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
