---
title: Jak utworzyć nową metodę dla przewodnika C# programowania
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705655"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="194d2-102">Jak utworzyć nową metodę dla wyliczenia (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="194d2-102">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="194d2-103">Można użyć metod rozszerzających, aby dodać funkcje specyficzne dla określonego typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="194d2-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="194d2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="194d2-104">Example</span></span>  
 <span data-ttu-id="194d2-105">W poniższym przykładzie Wyliczenie `Grades` reprezentuje możliwe klasy liter, które student może otrzymać w klasie.</span><span class="sxs-lookup"><span data-stu-id="194d2-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="194d2-106">Metoda rozszerzająca o nazwie `Passing` jest dodawana do typu `Grades`, tak aby każde wystąpienie tego typu było teraz "znane", niezależnie od tego, czy reprezentuje ona przewagę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="194d2-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="194d2-107">Należy zauważyć, że Klasa `Extensions` również zawiera zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="194d2-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="194d2-108">Pokazuje to, że w tle metody rozszerzające są wywoływane bezpośrednio w klasie statycznej, w której są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="194d2-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194d2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="194d2-109">See also</span></span>

- [<span data-ttu-id="194d2-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="194d2-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="194d2-111">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="194d2-111">Extension Methods</span></span>](./extension-methods.md)
