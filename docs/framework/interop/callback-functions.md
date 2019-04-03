---
title: Funkcje wywołania zwrotnego
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81a502ab3c0f9f2faf4685c5d61c66f2eab83e7f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820888"
---
# <a name="callback-functions"></a><span data-ttu-id="04e2c-102">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="04e2c-102">Callback Functions</span></span>
<span data-ttu-id="04e2c-103">Funkcja wywołania zwrotnego jest kod w zarządzanej aplikacji, która pomaga niezarządzanych funkcji DLL ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="04e2c-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="04e2c-104">Wywołania do funkcji wywołania zwrotnego przekazać pośrednio z aplikacji zarządzanych, za pomocą funkcji DLL i z powrotem do zarządzaną implementację.</span><span class="sxs-lookup"><span data-stu-id="04e2c-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="04e2c-105">Niektóre z wielu funkcji DLL o nazwie z platformą wywołania wymagają funkcji wywołania zwrotnego w kodzie zarządzanym działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="04e2c-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="04e2c-106">Aby wywołać większość funkcji DLL z kodu zarządzanego, tworzenie zarządzanych definicji funkcji, a następnie wywołać ją.</span><span class="sxs-lookup"><span data-stu-id="04e2c-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="04e2c-107">Ten proces jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="04e2c-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="04e2c-108">Za pomocą funkcji biblioteki DLL, która wymaga funkcji wywołania zwrotnego ma kilka dodatkowych kroków.</span><span class="sxs-lookup"><span data-stu-id="04e2c-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="04e2c-109">Najpierw należy określić, czy funkcja wymaga wywołania zwrotnego, analizując w dokumentacji dotyczącej funkcji.</span><span class="sxs-lookup"><span data-stu-id="04e2c-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="04e2c-110">Następnie należy utworzyć funkcję wywołania zwrotnego w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04e2c-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="04e2c-111">Na koniec wywołania funkcji DLL przekazywania wskaźnika do funkcji wywołania zwrotnego jako argument.</span><span class="sxs-lookup"><span data-stu-id="04e2c-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> 
 
 <span data-ttu-id="04e2c-112">Poniższa ilustracja zawiera podsumowanie kroków funkcji i implementacji wywołania zwrotnego:</span><span class="sxs-lookup"><span data-stu-id="04e2c-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagram przedstawiający platformy wywołania zwrotnego procesu.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="04e2c-114">Funkcje wywołania zwrotnego to idealne rozwiązanie w sytuacjach, w których zadanie jest wykonywane wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="04e2c-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="04e2c-115">Inny wspólne użycie jest przy użyciu funkcji wyliczania, takich jak **EnumFontFamilies**, **EnumPrinters**, i **EnumWindows** w interfejsie API Windows.</span><span class="sxs-lookup"><span data-stu-id="04e2c-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="04e2c-116">**EnumWindows** funkcja wylicza wszystkie istniejące systemu windows na komputerze, w wywołaniu funkcji wywołania zwrotnego do wykonywania zadań na każde okno.</span><span class="sxs-lookup"><span data-stu-id="04e2c-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="04e2c-117">Aby uzyskać instrukcje i przykłady, zobacz [jak: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="04e2c-117">For instructions and an example, see [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e2c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04e2c-118">See also</span></span>
- [<span data-ttu-id="04e2c-119">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="04e2c-119">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)
- [<span data-ttu-id="04e2c-120">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="04e2c-120">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
