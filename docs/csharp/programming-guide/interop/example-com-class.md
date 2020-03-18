---
title: Przykładowa klasa COM — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712081"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="355c0-102">Klasa COM — Przykład (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="355c0-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="355c0-103">Poniżej przedstawiono przykład klasy, które można udostępnić jako com obiektu.</span><span class="sxs-lookup"><span data-stu-id="355c0-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="355c0-104">Po umieszczeniu tego kodu w pliku .cs i dodaniu do projektu ustaw właściwość **Zarejestruj dla COM Interop** na **True**.</span><span class="sxs-lookup"><span data-stu-id="355c0-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="355c0-105">Aby uzyskać więcej informacji, zobacz [Jak: Zarejestrować składnik dla COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="355c0-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="355c0-106">Wystawianie obiektów Visual C# do com wymaga deklarowania interfejsu klasy, interfejs zdarzeń, jeśli jest to wymagane, a sama klasa.</span><span class="sxs-lookup"><span data-stu-id="355c0-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="355c0-107">Członkowie klasy muszą przestrzegać tych zasad, aby były widoczne dla COM:</span><span class="sxs-lookup"><span data-stu-id="355c0-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="355c0-108">Klasa musi być publiczna.</span><span class="sxs-lookup"><span data-stu-id="355c0-108">The class must be public.</span></span>  
  
- <span data-ttu-id="355c0-109">Właściwości, metody i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="355c0-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="355c0-110">Właściwości i metody muszą być zadeklarowane w interfejsie klasy.</span><span class="sxs-lookup"><span data-stu-id="355c0-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="355c0-111">Zdarzenia muszą być zadeklarowane w interfejsie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="355c0-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="355c0-112">Inne elementy publiczne w klasie, które nie są zadeklarowane w tych interfejsach nie będą widoczne dla com, ale będą widoczne dla innych obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="355c0-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="355c0-113">Aby udostępnić właściwości i metody do com, należy zadeklarować je `DispId` w interfejsie klasy i oznaczyć je z atrybutem i zaimplementować je w klasie.</span><span class="sxs-lookup"><span data-stu-id="355c0-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="355c0-114">Kolejność, w jakiej elementy członkowskie są deklarowane w interfejsie jest kolejność używana dla tabeli vtable COM.</span><span class="sxs-lookup"><span data-stu-id="355c0-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="355c0-115">Aby udostępnić zdarzenia z klasy, należy zadeklarować je w `DispId` interfejsie zdarzeń i oznaczyć je atrybutem.</span><span class="sxs-lookup"><span data-stu-id="355c0-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="355c0-116">Klasa nie powinna implementować tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="355c0-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="355c0-117">Klasa implementuje interfejs klasy; można zaimplementować więcej niż jeden interfejs, ale pierwsza implementacja będzie domyślny interfejs klasy.</span><span class="sxs-lookup"><span data-stu-id="355c0-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="355c0-118">Zaimplementuj metody i właściwości udostępniane com tutaj.</span><span class="sxs-lookup"><span data-stu-id="355c0-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="355c0-119">Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie klasy.</span><span class="sxs-lookup"><span data-stu-id="355c0-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="355c0-120">Ponadto zadeklarować zdarzenia wywoływane przez klasę tutaj.</span><span class="sxs-lookup"><span data-stu-id="355c0-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="355c0-121">Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="355c0-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="355c0-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="355c0-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="355c0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="355c0-123">See also</span></span>

- [<span data-ttu-id="355c0-124">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="355c0-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="355c0-125">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="355c0-125">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="355c0-126">Strona kompilacji, Projektant projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="355c0-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
