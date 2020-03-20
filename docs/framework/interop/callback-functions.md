---
title: Funkcje wywołania zwrotnego
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 8b8bb4dff4f73247282060c0b4fd778ae0169b1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181518"
---
# <a name="callback-functions"></a><span data-ttu-id="4b3fd-102">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4b3fd-102">Callback Functions</span></span>
<span data-ttu-id="4b3fd-103">Funkcja wywołania zwrotnego to kod w ramach zarządzanej aplikacji, który pomaga niezarządzanej funkcji DLL wykonać zadanie.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="4b3fd-104">Wywołania funkcji wywołania zwrotnego przechodzą pośrednio z zarządzanej aplikacji, za pośrednictwem funkcji DLL i z powrotem do implementacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="4b3fd-105">Niektóre z wielu funkcji DLL wywoływanych za pomocą wywołania platformy wymagają funkcji wywołania zwrotnego w kodzie zarządzanym, aby działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="4b3fd-106">Aby wywołać większość funkcji DLL z kodu zarządzanego, należy utworzyć zarządzaną definicję funkcji, a następnie wywołać go.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="4b3fd-107">Proces jest prosty.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="4b3fd-108">Za pomocą funkcji DLL, która wymaga funkcji wywołania zwrotnego ma kilka dodatkowych kroków.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="4b3fd-109">Najpierw należy określić, czy funkcja wymaga wywołania zwrotnego, patrząc na dokumentację funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="4b3fd-110">Następnie należy utworzyć funkcję wywołania zwrotnego w aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="4b3fd-111">Na koniec wywołać funkcję DLL, przekazując wskaźnik do funkcji wywołania zwrotnego jako argument.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="4b3fd-112">Na poniższej ilustracji podsumowano kroki funkcji wywołania zwrotnego i implementacji:</span><span class="sxs-lookup"><span data-stu-id="4b3fd-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagram przedstawiający proces wywołania zwrotnego na platformie.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="4b3fd-114">Funkcje wywołania zwrotnego są idealne do użycia w sytuacjach, w których zadanie jest wykonywane wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="4b3fd-115">Innym typowym zastosowaniem są funkcje wyliczenia, takie jak **EnumFontFamilies**, **EnumPrinters**i **EnumWindows** w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="4b3fd-116">**Funkcja EnumWindows wylicza** wszystkie istniejące okna na komputerze, wywołując funkcję wywołania zwrotnego w celu wykonania zadania w każdym oknie.</span><span class="sxs-lookup"><span data-stu-id="4b3fd-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="4b3fd-117">Aby uzyskać instrukcje i przykład, zobacz [Jak: Implementowanie funkcji wywołania zwrotnego](how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4b3fd-117">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3fd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b3fd-118">See also</span></span>

- [<span data-ttu-id="4b3fd-119">Porady: implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4b3fd-119">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="4b3fd-120">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="4b3fd-120">Calling a DLL Function</span></span>](calling-a-dll-function.md)
