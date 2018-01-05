---
title: "Funkcje wywołania zwrotnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4f39160e817ce04c5c15fb8299852a052d36c25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="callback-functions"></a><span data-ttu-id="40039-102">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="40039-102">Callback Functions</span></span>
<span data-ttu-id="40039-103">Funkcja wywołania zwrotnego jest kod w zarządzanej aplikacji, która pomaga w funkcji niezarządzanej DLL wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="40039-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="40039-104">Wywołania funkcji wywołania zwrotnego przekazywania pośrednio z zarządzanych aplikacji, za pomocą funkcji DLL i z powrotem do zarządzaną implementację.</span><span class="sxs-lookup"><span data-stu-id="40039-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="40039-105">Niektóre z wielu funkcji DLL wywoływana z platformą wywołania funkcja wywołania zwrotnego w kodzie zarządzanym do prawidłowego działania.</span><span class="sxs-lookup"><span data-stu-id="40039-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="40039-106">Aby wywołać większość funkcji DLL z kodu zarządzanego, tworzenie zarządzanej definicji funkcji, a następnie wywołać ją.</span><span class="sxs-lookup"><span data-stu-id="40039-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="40039-107">Proces jest prosta.</span><span class="sxs-lookup"><span data-stu-id="40039-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="40039-108">Przy użyciu funkcji DLL, która wymaga funkcji wywołania zwrotnego ma kilka dodatkowych kroków.</span><span class="sxs-lookup"><span data-stu-id="40039-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="40039-109">Najpierw należy określić, czy funkcja wymaga wywołania zwrotnego, analizując dokumentacji dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="40039-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="40039-110">Następnie należy utworzyć działanie funkcji wywołania zwrotnego w zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40039-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="40039-111">Ponadto wywołanie funkcji DLL przekazanie wskaźnika do funkcji wywołania zwrotnego jako argument.</span><span class="sxs-lookup"><span data-stu-id="40039-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> <span data-ttu-id="40039-112">Poniższej ilustracji przedstawiono następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="40039-112">The following illustration summarizes these steps.</span></span>  
  
 <span data-ttu-id="40039-113">![Wywołanie platformy wywołania zwrotnego](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span><span class="sxs-lookup"><span data-stu-id="40039-113">![Platform invoke callback](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span></span>  
<span data-ttu-id="40039-114">Funkcja wywołania zwrotnego i wdrażanie</span><span class="sxs-lookup"><span data-stu-id="40039-114">Callback function and implementation</span></span>  
  
 <span data-ttu-id="40039-115">Funkcje wywołania zwrotnego idealnie nadają się do użytku w sytuacjach, w których zadanie jest wykonywane wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="40039-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="40039-116">Innego użycie wspólnych jest wyliczenie funkcje takie jak **EnumFontFamilies**, **EnumPrinters**, i **EnumWindows** w interfejsie API Win32.</span><span class="sxs-lookup"><span data-stu-id="40039-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Win32 API.</span></span> <span data-ttu-id="40039-117">**EnumWindows** funkcja wylicza wszystkie istniejące systemu windows na komputerze, wywołanie funkcji wywołania zwrotnego do wykonywania zadań na każde okno.</span><span class="sxs-lookup"><span data-stu-id="40039-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="40039-118">Aby uzyskać instrukcje i przykładem, zobacz [porady: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="40039-118">For instructions and an example, see [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40039-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40039-119">See Also</span></span>  
 [<span data-ttu-id="40039-120">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="40039-120">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 [<span data-ttu-id="40039-121">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="40039-121">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
