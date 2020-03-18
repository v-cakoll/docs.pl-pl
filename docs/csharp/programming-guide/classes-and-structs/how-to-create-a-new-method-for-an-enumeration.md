---
title: Jak utworzyć nową metodę wyliczenia - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705655"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="b1cdc-102">Jak utworzyć nową metodę wyliczenia (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="b1cdc-102">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="b1cdc-103">Metody rozszerzenia służy do dodawania funkcji specyficznych dla określonego typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b1cdc-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1cdc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1cdc-104">Example</span></span>  
 <span data-ttu-id="b1cdc-105">W poniższym `Grades` przykładzie wyliczenie reprezentuje możliwe oceny liter, które uczeń może otrzymać w klasie.</span><span class="sxs-lookup"><span data-stu-id="b1cdc-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="b1cdc-106">Metoda rozszerzenia `Passing` o nazwie `Grades` jest dodawany do typu, tak aby każde wystąpienie tego typu teraz "wie", czy reprezentuje ocenę przekazywania, czy nie.</span><span class="sxs-lookup"><span data-stu-id="b1cdc-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="b1cdc-107">Należy zauważyć, że `Extensions` klasa zawiera również zmienną statyczną, która jest aktualizowana dynamicznie i że zwracana wartość metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b1cdc-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="b1cdc-108">Pokazuje to, że w tle metody rozszerzenia są wywoływane bezpośrednio na klasy statycznej, w której są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="b1cdc-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cdc-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1cdc-109">See also</span></span>

- [<span data-ttu-id="b1cdc-110">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b1cdc-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b1cdc-111">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="b1cdc-111">Extension Methods</span></span>](./extension-methods.md)
