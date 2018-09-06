---
title: Dane użytkownika w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- Windows Forms, user input
- mouse input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
ms.assetid: 1486075f-1e06-4c9e-82c6-f948331db6d6
ms.openlocfilehash: fef51f57dd3c14c91572041a72c805823d6019a3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037036"
---
# <a name="user-input-in-windows-forms"></a><span data-ttu-id="16b6e-102">Dane użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="16b6e-102">User Input in Windows Forms</span></span>
<span data-ttu-id="16b6e-103">Windows Forms zawiera model danych wejściowych użytkownika na podstawie zdarzeń, które są wywoływane podczas przetwarzania pokrewne wiadomości Windows.</span><span class="sxs-lookup"><span data-stu-id="16b6e-103">Windows Forms includes a user input model based on events that are raised while processing related Windows messages.</span></span> <span data-ttu-id="16b6e-104">Tematy w tej sekcji udostępniają informacje dotyczące klawiatury i myszy dane wejściowe użytkownika, wraz z przykładami kodu, które pokazują, jak do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="16b6e-104">The topics in this section provide information on mouse and keyboard user input, including code examples that demonstrate how to perform specific tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16b6e-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="16b6e-105">In This Section</span></span>  
 [<span data-ttu-id="16b6e-106">Wprowadzanie przez użytkownika w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16b6e-106">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="16b6e-107">Zawiera omówienie zdarzenia wejściowe użytkownika i metody, które przetwarzają komunikatów Windows.</span><span class="sxs-lookup"><span data-stu-id="16b6e-107">Provides an overview of user input events and the methods that process Windows messages.</span></span>  
  
 [<span data-ttu-id="16b6e-108">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16b6e-108">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="16b6e-109">Zawiera informacje dotyczące obsługi różnych typów kluczy i zdarzeń klawiatury komunikatu z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="16b6e-109">Provides information on keyboard message handling, the different types of keys, and the keyboard events.</span></span>  
  
 [<span data-ttu-id="16b6e-110">Wprowadzanie za pomocą myszy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16b6e-110">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="16b6e-111">Zawiera informacje dotyczące mysz, zdarzeń i inne powiązane myszy funkcje, w tym kursory myszy i przechwytywanie myszy.</span><span class="sxs-lookup"><span data-stu-id="16b6e-111">Provides information on the mouse events and other mouse-related features, including mouse cursors and mouse capture.</span></span>  
  
 [<span data-ttu-id="16b6e-112">Instrukcje: symulowanie zdarzeń myszy i klawiatury w kodzie</span><span class="sxs-lookup"><span data-stu-id="16b6e-112">How to: Simulate Mouse and Keyboard Events in Code</span></span>](../../../docs/framework/winforms/how-to-simulate-mouse-and-keyboard-events-in-code.md)  
 <span data-ttu-id="16b6e-113">Pokazuje kilka różnych sposobów, aby programowo symulować myszy i klawiatury.</span><span class="sxs-lookup"><span data-stu-id="16b6e-113">Demonstrates several different ways to programmatically simulate mouse and keyboard input.</span></span>  
  
 [<span data-ttu-id="16b6e-114">Instrukcje: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16b6e-114">How to: Handle User Input Events in Windows Forms Controls</span></span>](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md)  
 <span data-ttu-id="16b6e-115">Przedstawia informacje o przykładu kodu, który obsługuje większość zdarzenia wejściowe użytkownika i raportuje informacje dotyczące każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="16b6e-115">Presents a code example that handles most user input events and reports information about each event.</span></span>  
  
 [<span data-ttu-id="16b6e-116">Weryfikacja danych użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16b6e-116">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 <span data-ttu-id="16b6e-117">W tym artykule opisano metody, aby sprawdzić poprawność danych wejściowych użytkownika w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16b6e-117">Describes the methods to validate user input in Windows Forms applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16b6e-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="16b6e-118">Related Sections</span></span>  
 <span data-ttu-id="16b6e-119">Zobacz też [tworzenie obsługi zdarzeń w formularzach Windows Forms](https://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="16b6e-119">Also see [Creating Event Handlers in Windows Forms](https://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span></span>
