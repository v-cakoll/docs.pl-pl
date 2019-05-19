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
ms.openlocfilehash: e90e1d6643a30c1d2f4438e77317a2348b07fd71
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882423"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="23b44-102">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="23b44-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="23b44-103">Program obsługi zdarzeń jest procedurą w kodzie, który określa, jakie akcje są wykonywane, gdy wystąpi zdarzenie, takie jak kiedy użytkownik kliknie przycisk lub kolejka komunikatów odbiera komunikat.</span><span class="sxs-lookup"><span data-stu-id="23b44-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="23b44-104">Gdy zdarzenie jest wywoływane, program obsługi zdarzeń lub programów obsługi, otrzymają zdarzenie, które są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="23b44-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="23b44-105">Zdarzenia mogą być przypisane do wielu obsług i metod, które obsługują określonych zdarzeń można zmienić dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="23b44-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="23b44-106">Umożliwia także Windows Forms Designer w programie Visual Studio do tworzenia programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23b44-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="23b44-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="23b44-107">In This Section</span></span>

 <span data-ttu-id="23b44-108">[Przegląd zdarzeń](events-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="23b44-108">[Events Overview](events-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="23b44-109">Wyjaśnia model zdarzeń i rolę delegatów.</span><span class="sxs-lookup"><span data-stu-id="23b44-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="23b44-110">[Przegląd obsługi zdarzeń](event-handlers-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="23b44-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="23b44-111">W tym artykule opisano sposób obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23b44-111">Describes how to handle events.</span></span>

 <span data-ttu-id="23b44-112">[Instrukcje: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="23b44-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span></span>
 <span data-ttu-id="23b44-113">Zawiera wskazówki dotyczące odpowiadanie na zdarzenia system lub użytkownik dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="23b44-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="23b44-114">[Instrukcje: Łączenie wielu zdarzeń jedną procedurą obsługi zdarzeń w formularzach Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="23b44-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="23b44-115">Zawiera wskazówki dotyczące przypisywania taką samą funkcjonalność do wielu kontrolek za pomocą zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23b44-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="23b44-116">[Kolejność zdarzeń w formularzach Windows Forms](order-of-events-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="23b44-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="23b44-117">W tym artykule opisano, w kolejności, w której zdarzenia są wywoływane w kontrolkach formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="23b44-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="23b44-118">[Instrukcje: Tworzenie przy użyciu programów obsługi zdarzeń projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) opisano, jak używać programu Windows Forms Designer do tworzenia programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23b44-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="23b44-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="23b44-119">Related Sections</span></span>

 <span data-ttu-id="23b44-120">[Zdarzenia](../../standard/events/index.md)\\</span><span class="sxs-lookup"><span data-stu-id="23b44-120">[Events](../../standard/events/index.md)\\</span></span>
 <span data-ttu-id="23b44-121">Łącza do tematów, obsługa i wywoływanie zdarzeń przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23b44-121">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="23b44-122">[Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span><span class="sxs-lookup"><span data-stu-id="23b44-122">[Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span></span>
 <span data-ttu-id="23b44-123">Zawiera listę typowych problemów z programu obsługi zdarzeń w składników odziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="23b44-123">Lists common issues that occur with event handlers in inherited components.</span></span>
