---
title: Tworzenie nowych ciągów w .NET
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
ms.openlocfilehash: ef65c50111d6ba91ab70d0b9c8cb90c606f9366c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103819"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="57da8-102">Tworzenie nowych ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="57da8-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="57da8-103">.NET Framework umożliwia ciągi do utworzenia przy użyciu prostego przypisania, a także przeciążenia konstruktora klasy do obsługi tworzenia ciągów przy użyciu wielu różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="57da8-103">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="57da8-104">.NET Framework udostępnia również kilka <xref:System.String?displayProperty=nameWithType> metod w klasie, które tworzą nowe obiekty ciągu, łącząc kilka ciągów, tablicciągów lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="57da8-104">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="57da8-105">Tworzenie ciągów przy użyciu przypisania</span><span class="sxs-lookup"><span data-stu-id="57da8-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="57da8-106">Najprostszym sposobem utworzenia <xref:System.String> nowego obiektu jest po prostu <xref:System.String> przypisać literał ciągu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="57da8-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="57da8-107">Tworzenie ciągów przy użyciu konstruktora klas</span><span class="sxs-lookup"><span data-stu-id="57da8-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="57da8-108">Można użyć przeciążenia <xref:System.String> konstruktora klasy do tworzenia ciągów z tablic znaków.</span><span class="sxs-lookup"><span data-stu-id="57da8-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="57da8-109">Można również utworzyć nowy ciąg, powielając określony znak określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="57da8-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="57da8-110">Metody, które zwracają ciągi</span><span class="sxs-lookup"><span data-stu-id="57da8-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="57da8-111">W poniższej tabeli wymieniono kilka przydatnych metod, które zwracają nowe obiekty ciągu.</span><span class="sxs-lookup"><span data-stu-id="57da8-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="57da8-112">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="57da8-112">Method name</span></span>|<span data-ttu-id="57da8-113">Użycie</span><span class="sxs-lookup"><span data-stu-id="57da8-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="57da8-114">Tworzy sformatowany ciąg z zestawu obiektów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="57da8-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="57da8-115">Tworzy ciągi z dwóch lub więcej ciągów.</span><span class="sxs-lookup"><span data-stu-id="57da8-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="57da8-116">Tworzy nowy ciąg, łącząc tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="57da8-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="57da8-117">Tworzy nowy ciąg, wstawiając ciąg do określonego indeksu istniejącego ciągu.</span><span class="sxs-lookup"><span data-stu-id="57da8-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="57da8-118">Kopiuje określone znaki w ciągu do określonej pozycji w tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="57da8-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="57da8-119">Format</span><span class="sxs-lookup"><span data-stu-id="57da8-119">Format</span></span>  
 <span data-ttu-id="57da8-120">Za pomocą metody **String.Format** można tworzyć sformatowane ciągi i łączenie ciągów reprezentujących wiele obiektów.</span><span class="sxs-lookup"><span data-stu-id="57da8-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="57da8-121">Ta metoda automatycznie konwertuje dowolny przekazany obiekt na ciąg.</span><span class="sxs-lookup"><span data-stu-id="57da8-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="57da8-122">Na przykład jeśli aplikacja musi wyświetlać wartość **Int32** i **DateTime** wartość dla użytkownika, można łatwo skonstruować ciąg do reprezentowania tych wartości przy użyciu **Format** metody.</span><span class="sxs-lookup"><span data-stu-id="57da8-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="57da8-123">Aby uzyskać informacje na temat konwencji formatowania używanych z tą metodą, zobacz sekcję [dotyczącą formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="57da8-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="57da8-124">W poniższym przykładzie użyto **Metody Format** do utworzenia ciągu, który używa zmiennej całkowitej.</span><span class="sxs-lookup"><span data-stu-id="57da8-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="57da8-125">W tym<xref:System.DateTime.Now%2A?displayProperty=nameWithType> przykładzie wyświetla bieżącą datę i godzinę w sposób określony przez kulturę skojarzoną z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="57da8-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="57da8-126">Concat</span><span class="sxs-lookup"><span data-stu-id="57da8-126">Concat</span></span>  
 <span data-ttu-id="57da8-127">**String.Concat** Metoda może służyć do łatwego tworzenia nowego obiektu ciągu z dwóch lub więcej istniejących obiektów.</span><span class="sxs-lookup"><span data-stu-id="57da8-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="57da8-128">Zapewnia niezależny od języka sposób łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="57da8-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="57da8-129">Ta metoda akceptuje dowolną klasę, która pochodzi z **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="57da8-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="57da8-130">Poniższy przykład tworzy ciąg z dwóch istniejących obiektów ciągu i znak oddzielający.</span><span class="sxs-lookup"><span data-stu-id="57da8-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="57da8-131">Join</span><span class="sxs-lookup"><span data-stu-id="57da8-131">Join</span></span>  
 <span data-ttu-id="57da8-132">**String.Join** Metoda tworzy nowy ciąg z tablicy ciągów i ciąg separatora.</span><span class="sxs-lookup"><span data-stu-id="57da8-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="57da8-133">Ta metoda jest przydatna, jeśli chcesz połączyć wiele ciągów razem, dzięki czemu lista może być oddzielone przecinkiem.</span><span class="sxs-lookup"><span data-stu-id="57da8-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="57da8-134">W poniższym przykładzie użyto spacji do powiązania tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="57da8-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="57da8-135">Insert</span><span class="sxs-lookup"><span data-stu-id="57da8-135">Insert</span></span>  
 <span data-ttu-id="57da8-136">**String.Insert** Metoda tworzy nowy ciąg, wstawiając ciąg do określonej pozycji w innym ciągu.</span><span class="sxs-lookup"><span data-stu-id="57da8-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="57da8-137">Ta metoda używa indeksu od zera.</span><span class="sxs-lookup"><span data-stu-id="57da8-137">This method uses a zero-based index.</span></span> <span data-ttu-id="57da8-138">Poniższy przykład wstawia ciąg do piątej `MyString` pozycji indeksu i tworzy nowy ciąg z tą wartością.</span><span class="sxs-lookup"><span data-stu-id="57da8-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="57da8-139">Copyto</span><span class="sxs-lookup"><span data-stu-id="57da8-139">CopyTo</span></span>  
 <span data-ttu-id="57da8-140">Metoda **String.CopyTo** kopiuje fragmenty ciągu do tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="57da8-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="57da8-141">Można określić zarówno indeks początkowy ciągu, jak i liczbę znaków do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="57da8-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="57da8-142">Ta metoda pobiera indeks źródłowy, tablicę znaków, indeks docelowy i liczbę znaków do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="57da8-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="57da8-143">Wszystkie indeksy są oparte na zeru.</span><span class="sxs-lookup"><span data-stu-id="57da8-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="57da8-144">W poniższym przykładzie użyto **CopyTo** metody skopiować znaki słowa "Hello" z obiektu ciągu do pierwszej pozycji indeksu tablicy znaków.</span><span class="sxs-lookup"><span data-stu-id="57da8-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="57da8-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57da8-145">See also</span></span>

- [<span data-ttu-id="57da8-146">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="57da8-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="57da8-147">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="57da8-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
