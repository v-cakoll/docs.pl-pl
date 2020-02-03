---
title: Tworzenie programów obsługi zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 90acb3c7691acbcb528ae66692af67c2fb28eeaf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742331"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="e1a44-102">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e1a44-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="e1a44-103">Program obsługi zdarzeń to procedura w kodzie, która określa, jakie akcje są wykonywane w przypadku wystąpienia zdarzenia, na przykład gdy użytkownik kliknie przycisk lub kolejka komunikatów odbiera komunikat.</span><span class="sxs-lookup"><span data-stu-id="e1a44-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="e1a44-104">Gdy zdarzenie zostanie zgłoszone, program obsługi zdarzeń lub programy obsługi, które odbierają zdarzenie, są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="e1a44-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="e1a44-105">Zdarzenia mogą być przypisane do wielu programów obsługi, a metody obsługujące określone zdarzenia mogą być dynamicznie zmieniane.</span><span class="sxs-lookup"><span data-stu-id="e1a44-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="e1a44-106">Możesz również użyć Projektant formularzy systemu Windows w programie Visual Studio, aby utworzyć programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e1a44-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e1a44-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e1a44-107">In This Section</span></span>

 <span data-ttu-id="e1a44-108">[Przegląd zdarzeń](events-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="e1a44-108">[Events Overview](events-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="e1a44-109">Wyjaśnia model zdarzenia i rolę delegatów.</span><span class="sxs-lookup"><span data-stu-id="e1a44-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="e1a44-110">[Omówienie obsługi zdarzeń](event-handlers-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="e1a44-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="e1a44-111">Opisuje sposób obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e1a44-111">Describes how to handle events.</span></span>

 <span data-ttu-id="e1a44-112">[Instrukcje: tworzenie programów obsługi zdarzeń w czasie wykonywania dla Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="e1a44-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span></span>\
 <span data-ttu-id="e1a44-113">Oferuje instrukcje dotyczące dynamicznego reagowania na zdarzenia systemu lub użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e1a44-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="e1a44-114">[Instrukcje: łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="e1a44-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span></span>\
 <span data-ttu-id="e1a44-115">Daje wskazówki dotyczące przypisywania tych samych funkcji do wielu kontrolek za pomocą zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e1a44-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="e1a44-116">[Kolejność zdarzeń w Windows Forms](order-of-events-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="e1a44-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)</span></span>\
 <span data-ttu-id="e1a44-117">Opisuje kolejność, w której zdarzenia są zgłaszane w formantach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e1a44-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="e1a44-118">[Instrukcje: tworzenie programów obsługi zdarzeń przy użyciu narzędzia Projektant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Opisuje sposób używania Projektant formularzy systemu Windows do tworzenia programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e1a44-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e1a44-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e1a44-119">Related Sections</span></span>

 <span data-ttu-id="e1a44-120">\ [zdarzeń](../../standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="e1a44-120">[Events](../../standard/events/index.md)\</span></span>
 <span data-ttu-id="e1a44-121">Zawiera łącza do tematów dotyczących obsługi i wywoływania zdarzeń przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1a44-121">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="e1a44-122">[Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="e1a44-122">[Troubleshooting Inherited Event Handlers in Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span></span>\
 <span data-ttu-id="e1a44-123">Wyświetla listę typowych problemów występujących w przypadku programów obsługi zdarzeń w składnikach dziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="e1a44-123">Lists common issues that occur with event handlers in inherited components.</span></span>
