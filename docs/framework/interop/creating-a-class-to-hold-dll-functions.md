---
title: Tworzenie klasy utrzymującej funkcje DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b204eacd43db2c562fbe6d519b5fa91df3466cc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626412"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="d09ce-102">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="d09ce-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="d09ce-103">Zawijanie często używanych funkcji DLL w klasie zarządzanej jest efektywne podejście do hermetyzacji funkcje platformy.</span><span class="sxs-lookup"><span data-stu-id="d09ce-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="d09ce-104">Chociaż nie jest wymagane, aby to zrobić w każdym przypadku, zapewniając otoka klasy jest wygodne, ponieważ Definiowanie funkcji DLL może być skomplikowane i podatne na błędy.</span><span class="sxs-lookup"><span data-stu-id="d09ce-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="d09ce-105">Jeśli programujesz w języku Visual Basic lub C#, należy zadeklarować funkcji DLL w obrębie klasy lub w module języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d09ce-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="d09ce-106">W obrębie klasy można zdefiniować metody statycznej dla każdej funkcji DLL, który ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="d09ce-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="d09ce-107">Definicja może zawierać dodatkowe informacje, takie jak zestaw znaków lub konwencji wywoływania, używane do przekazywania argumentów metody; pomijając te informacje, możesz wybrać ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="d09ce-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="d09ce-108">Aby uzyskać pełną listę opcji deklaracji i domyślne ustawienia, zobacz [tworzenie prototypów w kodzie zarządzany](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="d09ce-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="d09ce-109">Po opakowaniu można wywołać metody w klasie, jak wywołanie metody statycznej na inne klasy.</span><span class="sxs-lookup"><span data-stu-id="d09ce-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="d09ce-110">Obsługuje wywołania platformy bazowej automatycznie wyeksportowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d09ce-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="d09ce-111">Podczas projektowania klas zarządzanych dla platformy wywołać, należy wziąć pod uwagę relacji między klasami i funkcji DLL.</span><span class="sxs-lookup"><span data-stu-id="d09ce-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="d09ce-112">Możesz na przykład:</span><span class="sxs-lookup"><span data-stu-id="d09ce-112">For example, you can:</span></span>  
  
- <span data-ttu-id="d09ce-113">Deklarowanie funkcji DLL w ramach istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="d09ce-113">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="d09ce-114">Utwórz klasę poszczególnych dla każdej funkcji DLL, utrzymywanie funkcji w izolowanej i łatwe do znalezienia.</span><span class="sxs-lookup"><span data-stu-id="d09ce-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="d09ce-115">Utwórz jedną klasę zbiór powiązanych funkcji DLL, które tworzą logiczne grupowanie i zmniejszyć obciążenie.</span><span class="sxs-lookup"><span data-stu-id="d09ce-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="d09ce-116">Możesz nazwać klasy i jego metod, jak należy.</span><span class="sxs-lookup"><span data-stu-id="d09ce-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="d09ce-117">Aby uzyskać przykłady pokazujące, jak utworzyć. Na podstawie NET deklaracje do użycia z platformą wywołania, zobacz [Marshaling danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="d09ce-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09ce-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d09ce-118">See also</span></span>

- [<span data-ttu-id="d09ce-119">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="d09ce-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="d09ce-120">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="d09ce-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [<span data-ttu-id="d09ce-121">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="d09ce-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="d09ce-122">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="d09ce-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
