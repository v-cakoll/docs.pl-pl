---
title: 'Porady: inicjowanie słownika przy użyciu inicjatora kolekcji (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 566acd21fb17247e7f5e42eb0eaa41b0beda6672
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520623"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="a5703-102">Porady: inicjowanie słownika przy użyciu inicjatora kolekcji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a5703-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="a5703-103">Element <xref:System.Collections.Generic.Dictionary`2> zawiera kolekcję par klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="a5703-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs.</span></span> <span data-ttu-id="a5703-104">Jego <xref:System.Collections.Generic.Dictionary`2.Add*> metoda przyjmuje dwa parametry: jeden dla klucza i jeden dla wartości.</span><span class="sxs-lookup"><span data-stu-id="a5703-104">Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="a5703-105">Aby zainicjować <xref:System.Collections.Generic.Dictionary`2>, lub dowolnej kolekcji którego `Add` metoda przyjmuje kilka parametrów, należy ująć każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5703-105">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5703-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5703-106">Example</span></span>  
 <span data-ttu-id="a5703-107">W poniższym przykładzie kodu <xref:System.Collections.Generic.Dictionary`2> jest inicjowany za pomocą wystąpienia typu `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="a5703-107">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="a5703-108">Należy pamiętać, dwie pary nawiasów klamrowych w każdym elemencie w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a5703-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="a5703-109">Najbardziej nawiasów klamrowych, należy ująć Inicjator obiektu `StudentName`, i najbardziej zewnętrznej nawiasów klamrowych ująć inicjator dla pary klucz/wartość, która zostanie dodana do `students` <xref:System.Collections.Generic.Dictionary`2>.</span><span class="sxs-lookup"><span data-stu-id="a5703-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary`2>.</span></span> <span data-ttu-id="a5703-110">Na koniec całej kolekcji inicjatora słownika jest ujęte w nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="a5703-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5703-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a5703-111">Compiling the Code</span></span>  
 <span data-ttu-id="a5703-112">Aby uruchomić ten kod, skopiuj i Wklej klasy Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5703-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="a5703-113">Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i ma odwołania do System.Core.dll i przy użyciu dyrektywy dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="a5703-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="a5703-114">Jeśli co najmniej jeden z tych wymagań brakuje z projektu, możesz je dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a5703-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5703-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5703-115">See Also</span></span>

- [<span data-ttu-id="a5703-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5703-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a5703-117">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="a5703-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
