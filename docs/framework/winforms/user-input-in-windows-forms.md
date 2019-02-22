---
title: Dane użytkownika w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- Windows Forms, user input
- mouse input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
ms.assetid: 1486075f-1e06-4c9e-82c6-f948331db6d6
ms.openlocfilehash: b422de09b41d72a680146192fd773767fe64e257
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664565"
---
# <a name="user-input-in-windows-forms"></a><span data-ttu-id="d6a81-102">Dane użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d6a81-102">User Input in Windows Forms</span></span>
<span data-ttu-id="d6a81-103">Windows Forms zawiera model danych wejściowych użytkownika na podstawie zdarzeń, które są wywoływane podczas przetwarzania pokrewne wiadomości Windows.</span><span class="sxs-lookup"><span data-stu-id="d6a81-103">Windows Forms includes a user input model based on events that are raised while processing related Windows messages.</span></span> <span data-ttu-id="d6a81-104">Tematy w tej sekcji udostępniają informacje dotyczące klawiatury i myszy dane wejściowe użytkownika, wraz z przykładami kodu, które pokazują, jak do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="d6a81-104">The topics in this section provide information on mouse and keyboard user input, including code examples that demonstrate how to perform specific tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6a81-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d6a81-105">In This Section</span></span>  
 [<span data-ttu-id="d6a81-106">Wprowadzanie przez użytkownika w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a81-106">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="d6a81-107">Zawiera omówienie zdarzenia wejściowe użytkownika i metody, które przetwarzają komunikatów Windows.</span><span class="sxs-lookup"><span data-stu-id="d6a81-107">Provides an overview of user input events and the methods that process Windows messages.</span></span>  
  
 [<span data-ttu-id="d6a81-108">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a81-108">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="d6a81-109">Zawiera informacje dotyczące obsługi różnych typów kluczy i zdarzeń klawiatury komunikatu z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="d6a81-109">Provides information on keyboard message handling, the different types of keys, and the keyboard events.</span></span>  
  
 [<span data-ttu-id="d6a81-110">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a81-110">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="d6a81-111">Zawiera informacje dotyczące mysz, zdarzeń i inne powiązane myszy funkcje, w tym kursory myszy i przechwytywanie myszy.</span><span class="sxs-lookup"><span data-stu-id="d6a81-111">Provides information on the mouse events and other mouse-related features, including mouse cursors and mouse capture.</span></span>  
  
 [<span data-ttu-id="d6a81-112">Instrukcje: Symulowanie zdarzeń myszy i klawiatury w kodzie</span><span class="sxs-lookup"><span data-stu-id="d6a81-112">How to: Simulate Mouse and Keyboard Events in Code</span></span>](../../../docs/framework/winforms/how-to-simulate-mouse-and-keyboard-events-in-code.md)  
 <span data-ttu-id="d6a81-113">Pokazuje kilka różnych sposobów, aby programowo symulować myszy i klawiatury.</span><span class="sxs-lookup"><span data-stu-id="d6a81-113">Demonstrates several different ways to programmatically simulate mouse and keyboard input.</span></span>  
  
 [<span data-ttu-id="d6a81-114">Instrukcje: Obsługa zdarzenia wejściowe użytkownika w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a81-114">How to: Handle User Input Events in Windows Forms Controls</span></span>](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md)  
 <span data-ttu-id="d6a81-115">Przedstawia informacje o przykładu kodu, który obsługuje większość zdarzenia wejściowe użytkownika i raportuje informacje dotyczące każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d6a81-115">Presents a code example that handles most user input events and reports information about each event.</span></span>  
  
 [<span data-ttu-id="d6a81-116">Weryfikacja danych użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a81-116">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 <span data-ttu-id="d6a81-117">W tym artykule opisano metody, aby sprawdzić poprawność danych wejściowych użytkownika w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d6a81-117">Describes the methods to validate user input in Windows Forms applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d6a81-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d6a81-118">Related Sections</span></span>  
 <span data-ttu-id="d6a81-119">Zobacz też [tworzenie obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d6a81-119">Also see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md).</span></span>
