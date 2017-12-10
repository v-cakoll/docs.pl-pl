---
title: "Porady: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c9da65958ce827fab642f4a6310d0c68dfb951a6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="abc24-102">Porady: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="abc24-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="abc24-103">W poniższym przykładzie prosty przedstawiono standardowy sposób, aby zadeklarować zdarzenia w klasie podstawowej, dzięki czemu również może być wywoływane z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="abc24-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="abc24-104">Ten wzorzec jest bardzo często używane w klasach formularzy systemu Windows w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="abc24-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="abc24-105">Podczas tworzenia klasy, która może służyć jako klasę podstawową innych klas należy rozważyć fakt, że zdarzenia są specjalny typ delegata, który można wywołać tylko z należące do klasy zadeklarowany je.</span><span class="sxs-lookup"><span data-stu-id="abc24-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="abc24-106">Klasy pochodne nie mogą wywoływać bezpośrednio zdarzenia, które są zadeklarowane w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="abc24-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="abc24-107">Jednak czasami może być zdarzenie, które może być zgłaszany tylko przez klasy podstawowej, w większości przypadków, należy włączyć klasy pochodnej w celu wywoływać zdarzeń klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="abc24-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="abc24-108">Aby to zrobić, można utworzyć chronionego wywoływanie metody w klasie podstawowej, która opakowuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="abc24-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="abc24-109">Przez wywołanie lub zastąpienie tego wywoływanie metody, klasy pochodne mogą wywoływać zdarzenia pośrednio.</span><span class="sxs-lookup"><span data-stu-id="abc24-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abc24-110">Nie deklaruje wirtualnego zdarzenia w klasie podstawowej i zastąpić je w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="abc24-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="abc24-111">Kompilator języka C# nie obsługuje te poprawnie i jest nieprzewidywalne czy subskrybentom pochodnej zdarzeń faktycznie będzie subskrybowanie zdarzeń klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="abc24-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abc24-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="abc24-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="abc24-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abc24-113">See Also</span></span>  
 [<span data-ttu-id="abc24-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="abc24-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="abc24-115">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="abc24-115">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="abc24-116">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="abc24-116">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="abc24-117">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="abc24-117">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="abc24-118">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="abc24-118">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
