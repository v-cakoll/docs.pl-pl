---
title: Tworzenie nowych ciągów w programie .NET
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
ms.openlocfilehash: a5dfe6429ac135202874f0524a252a7af900bd8d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279015"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="623f6-102">Tworzenie nowych ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="623f6-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="623f6-103">.NET Framework umożliwia tworzenie ciągów przy użyciu prostego przypisywania, a także przeciążenie konstruktora klasy do obsługi tworzenia ciągów przy użyciu wielu różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="623f6-103">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="623f6-104">.NET Framework udostępnia również kilka metod <xref:System.String?displayProperty=nameWithType> klasy, które tworzą nowe obiekty ciągu przez połączenie kilku ciągów, tablic ciągów lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="623f6-104">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="623f6-105">Tworzenie ciągów przy użyciu przypisania</span><span class="sxs-lookup"><span data-stu-id="623f6-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="623f6-106">Najprostszym sposobem utworzenia nowego <xref:System.String> obiektu jest przypisanie literału ciągu do <xref:System.String> obiektu.</span><span class="sxs-lookup"><span data-stu-id="623f6-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="623f6-107">Tworzenie ciągów przy użyciu konstruktora klasy</span><span class="sxs-lookup"><span data-stu-id="623f6-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="623f6-108">Można użyć przeciążenia <xref:System.String> konstruktora klasy do tworzenia ciągów z tablic znaków.</span><span class="sxs-lookup"><span data-stu-id="623f6-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="623f6-109">Możesz również utworzyć nowy ciąg, duplikując określony znak określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="623f6-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="623f6-110">Metody, które zwracają ciągi</span><span class="sxs-lookup"><span data-stu-id="623f6-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="623f6-111">Poniższa tabela zawiera kilka przydatnych metod, które zwracają nowe obiekty ciągu.</span><span class="sxs-lookup"><span data-stu-id="623f6-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="623f6-112">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="623f6-112">Method name</span></span>|<span data-ttu-id="623f6-113">Użycie</span><span class="sxs-lookup"><span data-stu-id="623f6-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="623f6-114">Kompiluje sformatowany ciąg z zestawu obiektów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="623f6-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="623f6-115">Kompiluje ciągi z dwóch lub więcej ciągów.</span><span class="sxs-lookup"><span data-stu-id="623f6-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="623f6-116">Kompiluje nowy ciąg, łącząc tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="623f6-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="623f6-117">Kompiluje nowy ciąg przez wstawienie ciągu do określonego indeksu istniejącego ciągu.</span><span class="sxs-lookup"><span data-stu-id="623f6-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="623f6-118">Kopiuje określone znaki w ciągu do określonej pozycji w tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="623f6-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="623f6-119">Format</span><span class="sxs-lookup"><span data-stu-id="623f6-119">Format</span></span>  
 <span data-ttu-id="623f6-120">Za pomocą metody **String. format** można tworzyć sformatowane ciągi i łączyć ciągi reprezentujące wiele obiektów.</span><span class="sxs-lookup"><span data-stu-id="623f6-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="623f6-121">Ta metoda automatycznie konwertuje każdy zakończony obiekt na ciąg.</span><span class="sxs-lookup"><span data-stu-id="623f6-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="623f6-122">Na przykład, jeśli w aplikacji musi być wyświetlana wartość **Int32** i wartość **DateTime** dla użytkownika, można łatwo skonstruować ciąg do reprezentowania tych wartości przy użyciu metody **Format** .</span><span class="sxs-lookup"><span data-stu-id="623f6-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="623f6-123">Aby uzyskać informacje na temat Konwencji formatowania używanych z tą metodą, zobacz sekcję dotyczącą [formatowania złożonego](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="623f6-123">For information about formatting conventions used with this method, see the section on [composite formatting](composite-formatting.md).</span></span>  
  
 <span data-ttu-id="623f6-124">W poniższym przykładzie zastosowano metodę **Format** , aby utworzyć ciąg, który używa zmiennej typu Integer.</span><span class="sxs-lookup"><span data-stu-id="623f6-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="623f6-125">W tym przykładzie <xref:System.DateTime.Now%2A?displayProperty=nameWithType> wyświetla bieżącą datę i godzinę w sposób określony przez kulturę skojarzoną z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="623f6-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="623f6-126">Concat</span><span class="sxs-lookup"><span data-stu-id="623f6-126">Concat</span></span>  
 <span data-ttu-id="623f6-127">Metoda **String. Concat** może służyć do łatwego tworzenia nowego obiektu ciągu z dwóch lub więcej istniejących obiektów.</span><span class="sxs-lookup"><span data-stu-id="623f6-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="623f6-128">Zapewnia on niezależny od języka sposób łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="623f6-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="623f6-129">Ta metoda akceptuje wszelkie klasy, które pochodzą z **obiektu System. Object**.</span><span class="sxs-lookup"><span data-stu-id="623f6-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="623f6-130">Poniższy przykład tworzy ciąg z dwóch istniejących obiektów String i oddzielający znak.</span><span class="sxs-lookup"><span data-stu-id="623f6-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="623f6-131">Join</span><span class="sxs-lookup"><span data-stu-id="623f6-131">Join</span></span>  
 <span data-ttu-id="623f6-132">Metoda **String. Join** tworzy nowy ciąg z tablicy ciągów i ciągu separatora.</span><span class="sxs-lookup"><span data-stu-id="623f6-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="623f6-133">Ta metoda jest przydatna, jeśli chcesz połączyć wiele ciągów ze sobą, tworząc listę, która może być oddzielona przecinkami.</span><span class="sxs-lookup"><span data-stu-id="623f6-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="623f6-134">Poniższy przykład używa spacji, aby powiązać tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="623f6-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="623f6-135">Insert</span><span class="sxs-lookup"><span data-stu-id="623f6-135">Insert</span></span>  
 <span data-ttu-id="623f6-136">Metoda **String. Insert** tworzy nowy ciąg przez wstawienie ciągu do określonej pozycji w innym ciągu.</span><span class="sxs-lookup"><span data-stu-id="623f6-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="623f6-137">Ta metoda używa indeksu na podstawie zera.</span><span class="sxs-lookup"><span data-stu-id="623f6-137">This method uses a zero-based index.</span></span> <span data-ttu-id="623f6-138">Poniższy przykład wstawia ciąg do piątej pozycji indeksu `MyString` i tworzy nowy ciąg z tą wartością.</span><span class="sxs-lookup"><span data-stu-id="623f6-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="623f6-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="623f6-139">CopyTo</span></span>  
 <span data-ttu-id="623f6-140">Metoda **String. CopyTo** kopiuje fragmenty ciągu do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="623f6-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="623f6-141">Można określić zarówno początkowy indeks ciągu, jak i liczbę znaków, które mają zostać skopiowane.</span><span class="sxs-lookup"><span data-stu-id="623f6-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="623f6-142">Ta metoda przyjmuje indeks źródłowy, tablicę znaków, indeks docelowy oraz liczbę znaków do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="623f6-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="623f6-143">Wszystkie indeksy są zależne od zera.</span><span class="sxs-lookup"><span data-stu-id="623f6-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="623f6-144">W poniższym przykładzie zastosowano metodę **CopyTo** , aby skopiować znaki wyrazu "Hello" z obiektu String do pierwszej pozycji indeksu tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="623f6-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="623f6-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="623f6-145">See also</span></span>

- [<span data-ttu-id="623f6-146">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="623f6-146">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="623f6-147">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="623f6-147">Composite Formatting</span></span>](composite-formatting.md)
