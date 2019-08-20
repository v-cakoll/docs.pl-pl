---
title: Przykładowa Klasa COM C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 461d5a2afb197596c1c52daeeca0583b7b5e9693
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589143"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="35b1a-102">Klasa COM — Przykład (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="35b1a-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="35b1a-103">Poniżej znajduje się przykład klasy, którą można uwidocznić jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="35b1a-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="35b1a-104">Gdy ten kod został umieszczony w pliku CS i dodany do projektu, ustaw właściwość **Register for com Interop** na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="35b1a-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="35b1a-105">Aby uzyskać więcej informacji, zobacz [jak: Zarejestruj składnik dla współdziałania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))z modelem com.</span><span class="sxs-lookup"><span data-stu-id="35b1a-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="35b1a-106">Uwidacznianie C# obiektów wizualnych do modelu COM wymaga zadeklarowania interfejsu klasy, interfejsu zdarzeń, jeśli jest to wymagane, i samej klasy.</span><span class="sxs-lookup"><span data-stu-id="35b1a-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="35b1a-107">Elementy członkowskie klasy muszą być zgodne z tymi regułami, aby były widoczne dla modelu COM:</span><span class="sxs-lookup"><span data-stu-id="35b1a-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="35b1a-108">Klasa musi być publiczna.</span><span class="sxs-lookup"><span data-stu-id="35b1a-108">The class must be public.</span></span>  
  
- <span data-ttu-id="35b1a-109">Właściwości, metody i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="35b1a-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="35b1a-110">Właściwości i metody muszą być zadeklarowane w interfejsie klasy.</span><span class="sxs-lookup"><span data-stu-id="35b1a-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="35b1a-111">Zdarzenia muszą być zadeklarowane w interfejsie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="35b1a-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="35b1a-112">Inne publiczne elementy członkowskie klasy, które nie są zadeklarowane w tych interfejsach, nie będą widoczne dla modelu COM, ale będą widoczne dla innych obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35b1a-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="35b1a-113">Aby uwidocznić właściwości i metody modelu COM, należy zadeklarować je w interfejsie klasy i oznaczyć je `DispId` atrybutami i zaimplementować je w klasie.</span><span class="sxs-lookup"><span data-stu-id="35b1a-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="35b1a-114">Kolejność, w której elementy członkowskie są zadeklarowane w interfejsie, jest kolejnością używaną w przypadku tablic wirtualnych COM.</span><span class="sxs-lookup"><span data-stu-id="35b1a-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="35b1a-115">Aby uwidocznić zdarzenia z klasy, należy je zadeklarować w interfejsie zdarzeń i oznaczyć je `DispId` atrybutami.</span><span class="sxs-lookup"><span data-stu-id="35b1a-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="35b1a-116">Klasa nie powinna implementować tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="35b1a-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="35b1a-117">Klasa implementuje interfejs klasy; może zaimplementować więcej niż jeden interfejs, ale Pierwsza implementacja będzie domyślnym interfejsem klasy.</span><span class="sxs-lookup"><span data-stu-id="35b1a-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="35b1a-118">W tym miejscu Zaimplementuj metody i właściwości uwidocznione w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="35b1a-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="35b1a-119">Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie klasy.</span><span class="sxs-lookup"><span data-stu-id="35b1a-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="35b1a-120">Ponadto w tym miejscu Zadeklaruj zdarzenia zgłoszone przez klasę.</span><span class="sxs-lookup"><span data-stu-id="35b1a-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="35b1a-121">Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="35b1a-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35b1a-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="35b1a-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="35b1a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35b1a-123">See also</span></span>

- [<span data-ttu-id="35b1a-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="35b1a-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="35b1a-125">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="35b1a-125">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="35b1a-126">Strona kompilacji, Projektant projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="35b1a-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
