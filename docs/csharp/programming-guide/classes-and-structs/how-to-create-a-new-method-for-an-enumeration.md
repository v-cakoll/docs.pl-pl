---
title: "Porady: utworzenie nowej metody wyliczania (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3cc15d24c9ba954a19fb87d4e364ac6e7f78e8b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="4ba88-102">Porady: utworzenie nowej metody wyliczania (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4ba88-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="4ba88-103">Metody rozszerzenia służy do dodawania funkcji charakterystycznej do wyliczenia określonego typu.</span><span class="sxs-lookup"><span data-stu-id="4ba88-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ba88-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ba88-104">Example</span></span>  
 <span data-ttu-id="4ba88-105">W poniższym przykładzie `Grades` wyliczenie reprezentuje klas możliwych list, które student może pojawić się w klasie.</span><span class="sxs-lookup"><span data-stu-id="4ba88-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="4ba88-106">Metody rozszerzenia o nazwie `Passing` jest dodawany do `Grades` wpisz, aby każde wystąpienie tego typu teraz "wie" czy reprezentuje klasy przekazywanie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="4ba88-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="4ba88-107">Należy pamiętać, że `Extensions` klasa zawiera także zmienną statyczną, która jest aktualizowana dynamicznie, i że zwracana wartość metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4ba88-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="4ba88-108">Oznacza to, że w tle metody rozszerzenia są wywoływane bezpośrednio w przypadku klasy statycznej, w którym są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="4ba88-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ba88-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4ba88-109">Compiling the Code</span></span>  
 <span data-ttu-id="4ba88-110">Aby uruchomić ten kod, skopiuj i wklej go do języka Visual C# console aplikacji projekt, który został utworzony w [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ba88-110">To run this code, copy and paste it into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="4ba88-111">Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i zawiera odwołania do System.Core.dll i `using` dyrektywy dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="4ba88-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="4ba88-112">Jeśli co najmniej jeden z tych wymagań brakuje z projektu, należy je dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="4ba88-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba88-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ba88-113">See Also</span></span>  
 [<span data-ttu-id="4ba88-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4ba88-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4ba88-115">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="4ba88-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
