---
title: Tworzenie nowych ciągów w programie .NET
description: Dowiedz się, jak tworzyć ciągi przy użyciu przypisań, konstruktorów klas lub metod system. String, które łączą kilka ciągów, tablic ciągów lub obiektów w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: b44d0f8e1717ead72e28f0be644644961d1482b6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596451"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="3ef7e-103">Tworzenie nowych ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="3ef7e-103">Creating New Strings in .NET</span></span>
<span data-ttu-id="3ef7e-104">.NET Framework umożliwia tworzenie ciągów przy użyciu prostego przypisywania, a także przeciążenie konstruktora klasy do obsługi tworzenia ciągów przy użyciu wielu różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-104">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="3ef7e-105">.NET Framework udostępnia również kilka metod <xref:System.String?displayProperty=nameWithType> klasy, które tworzą nowe obiekty ciągu przez połączenie kilku ciągów, tablic ciągów lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-105">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="3ef7e-106">Tworzenie ciągów przy użyciu przypisania</span><span class="sxs-lookup"><span data-stu-id="3ef7e-106">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="3ef7e-107">Najprostszym sposobem utworzenia nowego <xref:System.String> obiektu jest przypisanie literału ciągu do <xref:System.String> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-107">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="3ef7e-108">Tworzenie ciągów przy użyciu konstruktora klasy</span><span class="sxs-lookup"><span data-stu-id="3ef7e-108">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="3ef7e-109">Można użyć przeciążenia <xref:System.String> konstruktora klasy do tworzenia ciągów z tablic znaków.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-109">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="3ef7e-110">Możesz również utworzyć nowy ciąg, duplikując określony znak określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-110">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="3ef7e-111">Metody, które zwracają ciągi</span><span class="sxs-lookup"><span data-stu-id="3ef7e-111">Methods that Return Strings</span></span>  
 <span data-ttu-id="3ef7e-112">Poniższa tabela zawiera kilka przydatnych metod, które zwracają nowe obiekty ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-112">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="3ef7e-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="3ef7e-113">Method name</span></span>|<span data-ttu-id="3ef7e-114">Użycie</span><span class="sxs-lookup"><span data-stu-id="3ef7e-114">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="3ef7e-115">Kompiluje sformatowany ciąg z zestawu obiektów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-115">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="3ef7e-116">Kompiluje ciągi z dwóch lub więcej ciągów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-116">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="3ef7e-117">Kompiluje nowy ciąg, łącząc tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-117">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="3ef7e-118">Kompiluje nowy ciąg przez wstawienie ciągu do określonego indeksu istniejącego ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-118">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="3ef7e-119">Kopiuje określone znaki w ciągu do określonej pozycji w tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-119">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="3ef7e-120">Format</span><span class="sxs-lookup"><span data-stu-id="3ef7e-120">Format</span></span>  
 <span data-ttu-id="3ef7e-121">Za pomocą metody **String. format** można tworzyć sformatowane ciągi i łączyć ciągi reprezentujące wiele obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-121">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="3ef7e-122">Ta metoda automatycznie konwertuje każdy zakończony obiekt na ciąg.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-122">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="3ef7e-123">Na przykład, jeśli w aplikacji musi być wyświetlana wartość **Int32** i wartość **DateTime** dla użytkownika, można łatwo skonstruować ciąg do reprezentowania tych wartości przy użyciu metody **Format** .</span><span class="sxs-lookup"><span data-stu-id="3ef7e-123">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="3ef7e-124">Aby uzyskać informacje na temat Konwencji formatowania używanych z tą metodą, zobacz sekcję dotyczącą [formatowania złożonego](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="3ef7e-124">For information about formatting conventions used with this method, see the section on [composite formatting](composite-formatting.md).</span></span>  
  
 <span data-ttu-id="3ef7e-125">W poniższym przykładzie zastosowano metodę **Format** , aby utworzyć ciąg, który używa zmiennej typu Integer.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-125">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="3ef7e-126">W tym przykładzie <xref:System.DateTime.Now%2A?displayProperty=nameWithType> wyświetla bieżącą datę i godzinę w sposób określony przez kulturę skojarzoną z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-126">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="3ef7e-127">Concat</span><span class="sxs-lookup"><span data-stu-id="3ef7e-127">Concat</span></span>  
 <span data-ttu-id="3ef7e-128">Metoda **String. Concat** może służyć do łatwego tworzenia nowego obiektu ciągu z dwóch lub więcej istniejących obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-128">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="3ef7e-129">Zapewnia on niezależny od języka sposób łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-129">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="3ef7e-130">Ta metoda akceptuje wszelkie klasy, które pochodzą z **obiektu System. Object**.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-130">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="3ef7e-131">Poniższy przykład tworzy ciąg z dwóch istniejących obiektów String i oddzielający znak.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-131">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="3ef7e-132">Join</span><span class="sxs-lookup"><span data-stu-id="3ef7e-132">Join</span></span>  
 <span data-ttu-id="3ef7e-133">Metoda **String. Join** tworzy nowy ciąg z tablicy ciągów i ciągu separatora.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-133">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="3ef7e-134">Ta metoda jest przydatna, jeśli chcesz połączyć wiele ciągów ze sobą, tworząc listę, która może być oddzielona przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-134">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="3ef7e-135">Poniższy przykład używa spacji, aby powiązać tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-135">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="3ef7e-136">Insert</span><span class="sxs-lookup"><span data-stu-id="3ef7e-136">Insert</span></span>  
 <span data-ttu-id="3ef7e-137">Metoda **String. Insert** tworzy nowy ciąg przez wstawienie ciągu do określonej pozycji w innym ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-137">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="3ef7e-138">Ta metoda używa indeksu na podstawie zera.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-138">This method uses a zero-based index.</span></span> <span data-ttu-id="3ef7e-139">Poniższy przykład wstawia ciąg do piątej pozycji indeksu `MyString` i tworzy nowy ciąg z tą wartością.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-139">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="3ef7e-140">CopyTo</span><span class="sxs-lookup"><span data-stu-id="3ef7e-140">CopyTo</span></span>  
 <span data-ttu-id="3ef7e-141">Metoda **String. CopyTo** kopiuje fragmenty ciągu do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-141">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="3ef7e-142">Można określić zarówno początkowy indeks ciągu, jak i liczbę znaków, które mają zostać skopiowane.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-142">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="3ef7e-143">Ta metoda przyjmuje indeks źródłowy, tablicę znaków, indeks docelowy oraz liczbę znaków do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-143">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="3ef7e-144">Wszystkie indeksy są zależne od zera.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-144">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="3ef7e-145">W poniższym przykładzie zastosowano metodę **CopyTo** , aby skopiować znaki wyrazu "Hello" z obiektu String do pierwszej pozycji indeksu tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="3ef7e-145">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3ef7e-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ef7e-146">See also</span></span>

- [<span data-ttu-id="3ef7e-147">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="3ef7e-147">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="3ef7e-148">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="3ef7e-148">Composite Formatting</span></span>](composite-formatting.md)
