---
title: Klasa COM — Przykład (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 2dd1092d9c1f6bb7482c306339a3d7f6684940eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="d82d0-102">Klasa COM — Przykład (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d82d0-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="d82d0-103">Oto przykład klasy, która może narazić jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="d82d0-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="d82d0-104">Po ten kod został umieszczony w pliku .cs i dodane do projektu, ustawić **Zarejestruj dla międzyoperacyjności z modelem COM** właściwości **True**.</span><span class="sxs-lookup"><span data-stu-id="d82d0-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="d82d0-105">Aby uzyskać więcej informacji, zobacz [NIB: jak: zarejestrować składnika COM Interop](http://msdn.microsoft.com/library/4de7d474-56e8-4027-994d-d47ca4725c5e).</span><span class="sxs-lookup"><span data-stu-id="d82d0-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/library/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="d82d0-106">Udostępnianie obiektów Visual C# dla modelu COM wymaga deklarowanie interfejsu klasy, interfejsu zdarzenia w razie potrzeby i samej klasy.</span><span class="sxs-lookup"><span data-stu-id="d82d0-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="d82d0-107">Elementy członkowskie klasy, wykonaj te reguły mają być widoczne dla modelu COM:</span><span class="sxs-lookup"><span data-stu-id="d82d0-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="d82d0-108">Klasy muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="d82d0-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="d82d0-109">Właściwości, metod i zdarzeń muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="d82d0-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="d82d0-110">Właściwości i metody, musi zostać zadeklarowany w interfejsie klasa.</span><span class="sxs-lookup"><span data-stu-id="d82d0-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="d82d0-111">Zdarzenia musi zostać zadeklarowany w zdarzeniu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d82d0-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="d82d0-112">Inne publiczne elementy członkowskie w klasie, które nie są zadeklarowane w tych interfejsów nie będą widoczne dla modelu COM, ale będą one widoczne dla innych obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d82d0-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="d82d0-113">Do udostępnienia właściwości i metody dla modelu COM, należy zadeklarować je w interfejsie klasa i oznacz je za pomocą `DispId` atrybutu i ich wdrażania w klasie.</span><span class="sxs-lookup"><span data-stu-id="d82d0-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="d82d0-114">Kolejność, w jakiej elementy członkowskie są zadeklarowane w interfejsie jest kolejność używaną dla COM vtable.</span><span class="sxs-lookup"><span data-stu-id="d82d0-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="d82d0-115">Do udostępnienia zdarzenia z klasy, należy zadeklarować je dla interfejsu zdarzenia i oznacz je za pomocą `DispId` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d82d0-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="d82d0-116">Klasa nie powinny implementować ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="d82d0-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="d82d0-117">Klasa implementuje interfejs klasy; można zaimplementować więcej niż jeden interfejs, ale implementacja pierwszy będzie domyślnego interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="d82d0-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="d82d0-118">Implementuje metody i właściwości ujawniony dla modelu COM w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="d82d0-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="d82d0-119">One musi być oznaczona jako publiczna i musi być zgodna z deklaracjami w interfejsie klasa.</span><span class="sxs-lookup"><span data-stu-id="d82d0-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="d82d0-120">Ponadto należy zadeklarować zdarzenia wygenerowane przez klasę w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="d82d0-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="d82d0-121">One musi być oznaczona jako publiczna i musi być zgodna z deklaracji zdarzenia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d82d0-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d82d0-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="d82d0-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d82d0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d82d0-123">See Also</span></span>  
 [<span data-ttu-id="d82d0-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d82d0-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d82d0-125">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d82d0-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
 [<span data-ttu-id="d82d0-126">Strona kompilacji, Projektant projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="d82d0-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
