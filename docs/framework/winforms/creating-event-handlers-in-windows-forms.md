---
title: Tworzenie programów obsługi zdarzeń w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 96697fa54b569b6d1ce092ebfc76ef593f2ac66f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539157"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="b8b6e-102">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8b6e-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="b8b6e-103">Program obsługi zdarzeń jest procedurą w kodzie, który określa, jakie akcje są wykonywane, gdy wystąpi zdarzenie, na przykład gdy użytkownik kliknie przycisk lub kolejki komunikatów odbiera komunikat.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="b8b6e-104">Gdy zdarzenie jest zgłaszane, program obsługi zdarzeń lub obsługi, które odbierają zdarzenia są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="b8b6e-105">Zdarzenia mogą być przypisane do wielu obsług i metody obsługujące określonego zdarzenia można zmieniać dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="b8b6e-106">Projektant formularzy systemu Windows umożliwia również tworzenie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8b6e-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b8b6e-107">In This Section</span></span>  
 [<span data-ttu-id="b8b6e-108">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b8b6e-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="b8b6e-109">Opisano model zdarzeń oraz roli obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="b8b6e-110">Przegląd procedur obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b8b6e-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="b8b6e-111">Opisuje sposób obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="b8b6e-112">Instrukcje: tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8b6e-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="b8b6e-113">Zawiera wskazówki dotyczące odpowiadanie na zdarzenia system lub użytkownik dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="b8b6e-114">Instrukcje: łączenie wielu zdarzeń z jedną procedurą obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8b6e-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="b8b6e-115">Zawiera wskazówki dotyczące przypisywania te same funkcje do wielu formantów za pomocą zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="b8b6e-116">Kolejność zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8b6e-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="b8b6e-117">Opisuje kolejność, w której zdarzenia są generowane w formantach formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b8b6e-118">Porady: tworzenie obsługi zdarzeń przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="b8b6e-118">How to: Create Event Handlers Using the Designer</span></span>](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="b8b6e-119">Informacje dotyczące używania projektanta formularzy systemu Windows można utworzyć procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b8b6e-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b8b6e-120">Related Sections</span></span>  
 [<span data-ttu-id="b8b6e-121">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b8b6e-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="b8b6e-122">Zawiera łącza do tematów w Obsługa i wywoływanie zdarzeń przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8b6e-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="b8b6e-123">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8b6e-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="b8b6e-124">Wyświetla listę typowych problemów, które występują w przypadku obsługi zdarzeń w składników odziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="b8b6e-124">Lists common issues that occur with event handlers in inherited components.</span></span>
