---
title: Jak utworzyć nową metodę dla Przewodnik programowania w języku C#
description: Dowiedz się, jak przy użyciu metod rozszerzania dodać funkcję do wyliczenia w języku C#. Ten przykład pokazuje metodę rozszerzenia o nazwie Pass dla wyliczenia o nazwie klasy.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 6c01a73476e98e8344a7a8dc35a5fd80384fc7a2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864491"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="7d826-104">Jak utworzyć nową metodę dla wyliczenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7d826-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="7d826-105">Można użyć metod rozszerzających, aby dodać funkcje specyficzne dla określonego typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="7d826-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d826-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d826-106">Example</span></span>  
 <span data-ttu-id="7d826-107">W poniższym przykładzie `Grades` Wyliczenie reprezentuje możliwe klasy liter, które student może odebrać w klasie.</span><span class="sxs-lookup"><span data-stu-id="7d826-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="7d826-108">Metoda rozszerzenia o nazwie `Passing` jest dodawana do `Grades` typu, tak aby każde wystąpienie tego typu było teraz "znane", niezależnie od tego, czy reprezentuje ona przewagę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="7d826-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="7d826-109">Należy zauważyć, że `Extensions` Klasa zawiera również zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7d826-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="7d826-110">Pokazuje to, że w tle metody rozszerzające są wywoływane bezpośrednio w klasie statycznej, w której są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="7d826-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d826-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d826-111">See also</span></span>

- [<span data-ttu-id="7d826-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7d826-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7d826-113">Metody rozszerzające</span><span class="sxs-lookup"><span data-stu-id="7d826-113">Extension Methods</span></span>](./extension-methods.md)
