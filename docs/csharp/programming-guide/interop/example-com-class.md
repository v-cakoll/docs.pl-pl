---
title: "Klasa COM — Przykład (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 01b0a5b857171a1354a7dd6b518a7e151073ca32
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="95183-102">Klasa COM — Przykład (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="95183-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="95183-103">Oto przykład klasy, która może narazić jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="95183-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="95183-104">Po ten kod został umieszczony w pliku .cs i dodane do projektu, ustawić **Zarejestruj dla międzyoperacyjności z modelem COM** właściwości **True**.</span><span class="sxs-lookup"><span data-stu-id="95183-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="95183-105">Aby uzyskać więcej informacji, zobacz [NIB: jak: zarejestrować składnika COM Interop](http://msdn.microsoft.com/library/4de7d474-56e8-4027-994d-d47ca4725c5e).</span><span class="sxs-lookup"><span data-stu-id="95183-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/library/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="95183-106">Udostępnianie obiektów Visual C# dla modelu COM wymaga deklarowanie interfejsu klasy, interfejsu zdarzenia w razie potrzeby i samej klasy.</span><span class="sxs-lookup"><span data-stu-id="95183-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="95183-107">Elementy członkowskie klasy, wykonaj te reguły mają być widoczne dla modelu COM:</span><span class="sxs-lookup"><span data-stu-id="95183-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="95183-108">Klasy muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="95183-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="95183-109">Właściwości, metod i zdarzeń muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="95183-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="95183-110">Właściwości i metody, musi zostać zadeklarowany w interfejsie klasa.</span><span class="sxs-lookup"><span data-stu-id="95183-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="95183-111">Zdarzenia musi zostać zadeklarowany w zdarzeniu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95183-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="95183-112">Inne publiczne elementy członkowskie w klasie, które nie są zadeklarowane w tych interfejsów nie będą widoczne dla modelu COM, ale będą one widoczne dla innych obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95183-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="95183-113">Do udostępnienia właściwości i metody dla modelu COM, należy zadeklarować je w interfejsie klasa i oznacz je za pomocą `DispId` atrybutu i ich wdrażania w klasie.</span><span class="sxs-lookup"><span data-stu-id="95183-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="95183-114">Kolejność, w jakiej elementy członkowskie są zadeklarowane w interfejsie jest kolejność używaną dla COM vtable.</span><span class="sxs-lookup"><span data-stu-id="95183-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="95183-115">Do udostępnienia zdarzenia z klasy, należy zadeklarować je dla interfejsu zdarzenia i oznacz je za pomocą `DispId` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="95183-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="95183-116">Klasa nie powinny implementować ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="95183-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="95183-117">Klasa implementuje interfejs klasy; można zaimplementować więcej niż jeden interfejs, ale implementacja pierwszy będzie domyślnego interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="95183-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="95183-118">Implementuje metody i właściwości ujawniony dla modelu COM w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="95183-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="95183-119">One musi być oznaczona jako publiczna i musi być zgodna z deklaracjami w interfejsie klasa.</span><span class="sxs-lookup"><span data-stu-id="95183-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="95183-120">Ponadto należy zadeklarować zdarzenia wygenerowane przez klasę w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="95183-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="95183-121">One musi być oznaczona jako publiczna i musi być zgodna z deklaracji zdarzenia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95183-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95183-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="95183-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="95183-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95183-123">See Also</span></span>  
 [<span data-ttu-id="95183-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="95183-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="95183-125">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="95183-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
 [<span data-ttu-id="95183-126">Strona kompilacji, Projektant projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="95183-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
