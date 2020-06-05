---
title: Przycinanie i usuwanie znaków z ciągów w programie .NET
description: Dowiedz się, jak przyciąć spacje puste od początku lub końca ciągu lub usunąć dowolną liczbę spacji lub znaków z określonej pozycji w ciągu w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: 630fe6b51d151d1f1384f2e3cde62750c303d883
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446896"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="04098-103">Przycinanie i usuwanie znaków z ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="04098-103">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="04098-104">Jeśli analizujesz zdanie w poszczególnych słowach, możesz kończyć się wyrazami z pustymi spacjami (nazywanymi również białymi spacjami) na dowolnym końcu słowa.</span><span class="sxs-lookup"><span data-stu-id="04098-104">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="04098-105">W takiej sytuacji można użyć jednej z metod przycinania w klasie **System. String** , aby usunąć dowolną liczbę spacji lub innych znaków z określonej pozycji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-105">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="04098-106">W poniższej tabeli opisano dostępne metody przycinania.</span><span class="sxs-lookup"><span data-stu-id="04098-106">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="04098-107">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="04098-107">Method name</span></span>|<span data-ttu-id="04098-108">Użycie</span><span class="sxs-lookup"><span data-stu-id="04098-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="04098-109">Usuwa spacje lub znaki określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-109">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="04098-110">Usuwa znaki określone w tablicy znaków od końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-110">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="04098-111">Usuwa znaki określone w tablicy znaków od początku ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-111">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="04098-112">Usuwa określoną liczbę znaków z podanej pozycji indeksu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-112">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="04098-113">Trim</span><span class="sxs-lookup"><span data-stu-id="04098-113">Trim</span></span>

 <span data-ttu-id="04098-114">Można łatwo usunąć białe znaki z obu punktów końcowych ciągu za pomocą <xref:System.String.Trim%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04098-114">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="04098-115">Można również usunąć znaki określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-115">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="04098-116">Poniższy przykład usuwa znaki odstępu, kropki i gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="04098-116">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="04098-117">Metoda TrimEnd</span><span class="sxs-lookup"><span data-stu-id="04098-117">TrimEnd</span></span>

 <span data-ttu-id="04098-118">Metoda **String. TrimEnd** usuwa znaki z końca ciągu, tworząc nowy obiekt ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-118">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="04098-119">Tablica znaków jest przenoszona do tej metody w celu określenia znaków do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="04098-119">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="04098-120">Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="04098-120">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="04098-121">Przycinanie zostaje zatrzymane, gdy zostanie znaleziony znak nieokreślony w tablicy.</span><span class="sxs-lookup"><span data-stu-id="04098-121">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="04098-122">Poniższy przykład usuwa ostatnie litery ciągu przy użyciu metody **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="04098-122">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="04098-123">W tym przykładzie pozycja `'r'` znaku i `'W'` znaku jest odwrócona, aby zilustrować, że kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="04098-123">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="04098-124">Zauważ, że ten kod usuwa ostatni wyraz z `MyString` i części pierwszej.</span><span class="sxs-lookup"><span data-stu-id="04098-124">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="04098-125">Ten kod `He` jest wyświetlany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="04098-125">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="04098-126">Poniższy przykład usuwa ostatni wyraz ciągu przy użyciu metody **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="04098-126">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="04098-127">W tym kodzie przecinek następuje po słowie `Hello` i, ponieważ przecinek nie jest określony w tablicy znaków do przycinania, przycinanie następuje na przecinek.</span><span class="sxs-lookup"><span data-stu-id="04098-127">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="04098-128">Ten kod `Hello,` jest wyświetlany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="04098-128">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="04098-129">Metoda TrimStart</span><span class="sxs-lookup"><span data-stu-id="04098-129">TrimStart</span></span>

 <span data-ttu-id="04098-130">Metoda **String. TrimStart** jest podobna do metody **String. TrimEnd** , z tą różnicą, że tworzy nowy ciąg przez usunięcie znaków z początku istniejącego obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-130">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="04098-131">Tablica znaków jest przenoszona do metody **TrimStart** w celu określenia znaków do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="04098-131">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="04098-132">Podobnie jak w przypadku metody **TrimEnd** , kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="04098-132">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="04098-133">Przycinanie zostaje zatrzymane, gdy zostanie znaleziony znak nieokreślony w tablicy.</span><span class="sxs-lookup"><span data-stu-id="04098-133">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="04098-134">Poniższy przykład usuwa pierwsze słowo ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-134">The following example removes the first word of a string.</span></span> <span data-ttu-id="04098-135">W tym przykładzie pozycja `'l'` znaku i `'H'` znaku jest odwrócona, aby zilustrować, że kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="04098-135">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="04098-136">Ten kod `World!` jest wyświetlany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="04098-136">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="04098-137">Usuń</span><span class="sxs-lookup"><span data-stu-id="04098-137">Remove</span></span>

 <span data-ttu-id="04098-138"><xref:System.String.Remove%2A?displayProperty=nameWithType>Metoda usuwa określoną liczbę znaków, zaczynając od określonej pozycji w istniejącym ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-138">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="04098-139">Ta metoda przyjmuje indeks oparty na wartości zero.</span><span class="sxs-lookup"><span data-stu-id="04098-139">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="04098-140">Poniższy przykład usuwa dziesięć znaków z ciągu, zaczynając od pozycji piątej indeksu ciągu od zera.</span><span class="sxs-lookup"><span data-stu-id="04098-140">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="04098-141">Replace</span><span class="sxs-lookup"><span data-stu-id="04098-141">Replace</span></span>

 <span data-ttu-id="04098-142">Można również usunąć określony znak lub podciąg z ciągu, wywołując <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodę i określając pusty ciąg ( <xref:System.String.Empty?displayProperty=nameWithType> ) jako zamiennik.</span><span class="sxs-lookup"><span data-stu-id="04098-142">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="04098-143">Poniższy przykład usuwa wszystkie przecinki z ciągu.</span><span class="sxs-lookup"><span data-stu-id="04098-143">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="04098-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04098-144">See also</span></span>

- [<span data-ttu-id="04098-145">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="04098-145">Basic String Operations</span></span>](basic-string-operations.md)
