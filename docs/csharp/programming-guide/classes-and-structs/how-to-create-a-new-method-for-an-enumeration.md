---
title: 'Instrukcje: Utworzenie nowej metody wyliczania - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: f8495cd747cf895c4da34c216ba9285182890af1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238732"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="aca70-102">Instrukcje: Utworzenie nowej metody wyliczania (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="aca70-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="aca70-103">Metody rozszerzające umożliwia dodawanie funkcji charakterystycznej do typu określonego typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="aca70-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aca70-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aca70-104">Example</span></span>  
 <span data-ttu-id="aca70-105">W poniższym przykładzie `Grades` wyliczenie reprezentuje możliwe litery ocen, które student może pojawić się w klasie.</span><span class="sxs-lookup"><span data-stu-id="aca70-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="aca70-106">Metody rozszerzenia o nazwie `Passing` jest dodawany do `Grades` wpisz, aby każde wystąpienie tego typu teraz "wie" czy reprezentuje klasy przekazywanie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="aca70-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="aca70-107">Należy pamiętać, że `Extensions` klasa zawiera także zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana przez metoda rozszerzenia odzwierciedla bieżącą wartość tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="aca70-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="aca70-108">Oznacza to, że w tle metody rozszerzenia są wywoływane bezpośrednio na klasy statycznej, w której są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="aca70-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aca70-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="aca70-109">Compiling the Code</span></span>  
 <span data-ttu-id="aca70-110">Aby uruchomić ten kod, skopiuj i wklej go do programu Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aca70-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="aca70-111">Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i ma odwołania do System.Core.dll i `using` dyrektywy dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="aca70-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="aca70-112">Jeśli co najmniej jeden z tych wymagań brakuje z projektu, możesz je dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="aca70-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca70-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aca70-113">See Also</span></span>

- [<span data-ttu-id="aca70-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="aca70-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aca70-115">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="aca70-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
