---
title: "Tworzenie nowych ciągów w .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d000cd88fc9ee9fd48ef25e9bb4982688564a2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="f1030-102">Tworzenie nowych ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="f1030-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="f1030-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Umożliwia ciągów, które ma zostać utworzony przy użyciu przypisanie proste, a także overloads konstruktora klasy do obsługi tworzenia ciągu przy użyciu wielu różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="f1030-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="f1030-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Udostępnia kilka metod w <xref:System.String?displayProperty=nameWithType> klasy, która utworzyć nowe parametry obiektów przez łączenie wielu ciągów, tablic ciągów, ani obiektów.</span><span class="sxs-lookup"><span data-stu-id="f1030-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="f1030-105">Tworzenie ciągów za pomocą przypisania</span><span class="sxs-lookup"><span data-stu-id="f1030-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="f1030-106">Najprostszym sposobem, aby utworzyć nową <xref:System.String> obiektu jest po prostu przypisanie literału ciągu na <xref:System.String> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1030-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="f1030-107">Tworzenie ciągów za pomocą konstruktora klasy</span><span class="sxs-lookup"><span data-stu-id="f1030-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="f1030-108">Można użyć przeciążeń <xref:System.String> konstruktora klasy w celu utworzenia ciągów w tablice znaków.</span><span class="sxs-lookup"><span data-stu-id="f1030-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="f1030-109">Można również utworzyć nowe parametry, duplikując określonego znaku określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="f1030-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="f1030-110">Metody zwracające ciągów</span><span class="sxs-lookup"><span data-stu-id="f1030-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="f1030-111">W poniższej tabeli wymieniono kilka metod przydatne, które zwracają nowe obiekty ciągu.</span><span class="sxs-lookup"><span data-stu-id="f1030-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="f1030-112">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="f1030-112">Method name</span></span>|<span data-ttu-id="f1030-113">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="f1030-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="f1030-114">Tworzy ciąg sformatowany za pomocą zestawu wejściowego obiektów.</span><span class="sxs-lookup"><span data-stu-id="f1030-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="f1030-115">Tworzy ciągów z co najmniej dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="f1030-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="f1030-116">Tworzy nowe parametry, łącząc tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="f1030-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="f1030-117">Tworzy nowe parametry wstawiając ciąg do określonego indeksu istniejące parametry.</span><span class="sxs-lookup"><span data-stu-id="f1030-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="f1030-118">Kopiuje określone znaków w ciągu w określonej pozycji w tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="f1030-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="f1030-119">Format</span><span class="sxs-lookup"><span data-stu-id="f1030-119">Format</span></span>  
 <span data-ttu-id="f1030-120">Można użyć **String.Format** metody do tworzenia ciągi sformatowane i łączenie ciągów reprezentujących wielu obiektów.</span><span class="sxs-lookup"><span data-stu-id="f1030-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="f1030-121">Ta metoda powoduje automatyczną konwersję dowolnego przekazanego obiektu na ciąg.</span><span class="sxs-lookup"><span data-stu-id="f1030-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="f1030-122">Na przykład, jeśli aplikacja musi zawierać **Int32** wartość i **DateTime** wartość dla użytkownika, można łatwo utworzyć ciąg do reprezentowania te wartości przy użyciu **Format**metody.</span><span class="sxs-lookup"><span data-stu-id="f1030-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="f1030-123">Informacje na temat formatowania konwencje używane z tą metodą, zobacz sekcję dotyczącą [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="f1030-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="f1030-124">W poniższym przykładzie użyto **Format** metodę w celu utworzenia ciąg, który używa zmienna typu Liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="f1030-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="f1030-125">W tym przykładzie<xref:System.DateTime.Now%2A?displayProperty=nameWithType> Wyświetla bieżącą datę i godzinę w sposób określony przez kultury skojarzone z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="f1030-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="f1030-126">concat</span><span class="sxs-lookup"><span data-stu-id="f1030-126">Concat</span></span>  
 <span data-ttu-id="f1030-127">**String.concat —** — metoda pozwala łatwo utworzyć nowy obiekt ciągu z dwóch lub więcej istniejących obiektów.</span><span class="sxs-lookup"><span data-stu-id="f1030-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="f1030-128">Zapewnia sposób niezależny od języka aby ciągów.</span><span class="sxs-lookup"><span data-stu-id="f1030-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="f1030-129">Ta metoda przyjmuje dowolnej klasy, która jest pochodną **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="f1030-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="f1030-130">Poniższy przykład tworzy ciąg z dwóch istniejących obiektów ciągu i znak oddzielający.</span><span class="sxs-lookup"><span data-stu-id="f1030-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="f1030-131">Łączenie</span><span class="sxs-lookup"><span data-stu-id="f1030-131">Join</span></span>  
 <span data-ttu-id="f1030-132">**String.Join** metoda tworzy nowego ciągu z tablicy ciągów i ciąg separatora.</span><span class="sxs-lookup"><span data-stu-id="f1030-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="f1030-133">Ta metoda jest przydatna, jeśli chcesz łączenie wielu ciągów, tworzenie listy prawdopodobnie rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="f1030-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="f1030-134">W poniższym przykładzie użyto spację, aby powiązać tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="f1030-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="f1030-135">Insert</span><span class="sxs-lookup"><span data-stu-id="f1030-135">Insert</span></span>  
 <span data-ttu-id="f1030-136">**String.Insert** metoda tworzy nowy ciąg wstawiając ciąg do określonej pozycji w innym ciągu.</span><span class="sxs-lookup"><span data-stu-id="f1030-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="f1030-137">Ta metoda korzysta z indeksu.</span><span class="sxs-lookup"><span data-stu-id="f1030-137">This method uses a zero-based index.</span></span> <span data-ttu-id="f1030-138">Poniższy przykład wstawia ciąg do piątego indeks `MyString` i tworzy nowy ciąg o tej wartości.</span><span class="sxs-lookup"><span data-stu-id="f1030-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="f1030-139">Wykonanie operacji kopiowania</span><span class="sxs-lookup"><span data-stu-id="f1030-139">CopyTo</span></span>  
 <span data-ttu-id="f1030-140">**String.CopyTo** metody kopiuje części ciągu do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="f1030-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="f1030-141">Można określić indeksu początku ciąg i liczbę znaków do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="f1030-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="f1030-142">Ta metoda przyjmuje indeks źródła, tablicy znaków indeksu docelowego i liczbę znaków do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="f1030-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="f1030-143">Wszystkie indeksy są liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="f1030-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="f1030-144">W poniższym przykładzie użyto **CopyTo** metodę, aby skopiować znaki Word tekst "Hello" z ciągu obiektu na pierwszym miejscu indeksu tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="f1030-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f1030-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1030-145">See Also</span></span>  
 [<span data-ttu-id="f1030-146">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="f1030-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="f1030-147">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="f1030-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
