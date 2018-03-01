---
title: "Porady: inicjowanie słownika przy użyciu inicjatora kolekcji (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="2cb5e-102">Porady: inicjowanie słownika przy użyciu inicjatora kolekcji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2cb5e-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="2cb5e-103">A < xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add\* > metoda przyjmuje dwa parametry: jeden dla klucza i jeden dla wartości.</span><span class="sxs-lookup"><span data-stu-id="2cb5e-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add\*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="2cb5e-104">Aby zainicjować < xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Dodaj "metoda przyjmuje kilka parametrów, ujmij każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2cb5e-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb5e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2cb5e-105">Example</span></span>  
 <span data-ttu-id="2cb5e-106">W poniższym przykładzie kodu < xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName ".</span><span class="sxs-lookup"><span data-stu-id="2cb5e-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="2cb5e-107">Należy zwrócić uwagę dwie pary nawiasów klamrowych w każdym elementem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2cb5e-107">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="2cb5e-108">Najbardziej nawiasów klamrowych ujmij inicjatora obiektu dla `StudentName`, i nawiasy peryferyjnych ujmij inicjator dla pary klucza/wartości, który zostanie dodany do `students` <xref:System.Collections.Generic.Dictionary\`2>.</span><span class="sxs-lookup"><span data-stu-id="2cb5e-108">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary\`2>.</span></span> <span data-ttu-id="2cb5e-109">Na koniec całą kolekcję inicjatora słownika jest ujęta w nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="2cb5e-109">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2cb5e-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2cb5e-110">Compiling the Code</span></span>  
 <span data-ttu-id="2cb5e-111">Aby uruchomić ten kod, skopiuj i Wklej klasy w projektach Visual C# console aplikacji utworzony w [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2cb5e-111">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="2cb5e-112">Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i zawiera odwołania do System.Core.dll i przy użyciu dyrektywy dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="2cb5e-112">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="2cb5e-113">Jeśli co najmniej jeden z tych wymagań brakuje z projektu, należy je dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="2cb5e-113">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb5e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cb5e-114">See Also</span></span>  
 [<span data-ttu-id="2cb5e-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2cb5e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2cb5e-116">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2cb5e-116">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
