---
title: 'Instrukcje: Utwórz nową metodę dla przewodnika C# programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 99a2005e1a64fa214776145a903341fb162f0633
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597047"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="b964a-102">Instrukcje: Tworzenie nowej metody dla wyliczenia (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="b964a-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="b964a-103">Można użyć metod rozszerzających, aby dodać funkcje specyficzne dla określonego typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="b964a-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b964a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b964a-104">Example</span></span>  
 <span data-ttu-id="b964a-105">W poniższym przykładzie `Grades` Wyliczenie reprezentuje możliwe klasy liter, które student może odebrać w klasie.</span><span class="sxs-lookup"><span data-stu-id="b964a-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="b964a-106">Metoda rozszerzenia o nazwie `Passing` jest dodawana `Grades` do typu, tak aby każde wystąpienie tego typu było teraz "znane", niezależnie od tego, czy reprezentuje ona przewagę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="b964a-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="b964a-107">Należy zauważyć, `Extensions` że Klasa zawiera również zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b964a-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="b964a-108">Pokazuje to, że w tle metody rozszerzające są wywoływane bezpośrednio w klasie statycznej, w której są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="b964a-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b964a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b964a-109">See also</span></span>

- [<span data-ttu-id="b964a-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b964a-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b964a-111">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="b964a-111">Extension Methods</span></span>](./extension-methods.md)
