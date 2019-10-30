---
title: Przycinanie i usuwanie znaków z ciągów w programie .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c694a6792168f37e1f134cf965658e8a058e240a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037870"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="e3102-102">Przycinanie i usuwanie znaków z ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="e3102-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="e3102-103">Jeśli analizujesz zdanie w poszczególnych słowach, możesz kończyć się wyrazami z pustymi spacjami (nazywanymi również białymi spacjami) na dowolnym końcu słowa.</span><span class="sxs-lookup"><span data-stu-id="e3102-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="e3102-104">W takiej sytuacji można użyć jednej z metod przycinania w klasie **System. String** , aby usunąć dowolną liczbę spacji lub innych znaków z określonej pozycji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="e3102-105">W poniższej tabeli opisano dostępne metody przycinania.</span><span class="sxs-lookup"><span data-stu-id="e3102-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="e3102-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="e3102-106">Method name</span></span>|<span data-ttu-id="e3102-107">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="e3102-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="e3102-108">Usuwa spacje lub znaki określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="e3102-109">Usuwa znaki określone w tablicy znaków od końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="e3102-110">Usuwa znaki określone w tablicy znaków od początku ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="e3102-111">Usuwa określoną liczbę znaków z podanej pozycji indeksu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="e3102-112">Trim</span><span class="sxs-lookup"><span data-stu-id="e3102-112">Trim</span></span>

 <span data-ttu-id="e3102-113">Można łatwo usunąć białe znaki z obu punktów końcowych ciągu za pomocą metody <xref:System.String.Trim%2A?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e3102-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="e3102-114">Można również usunąć znaki określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="e3102-115">Poniższy przykład usuwa znaki odstępu, kropki i gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="e3102-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="e3102-116">Metoda TrimEnd</span><span class="sxs-lookup"><span data-stu-id="e3102-116">TrimEnd</span></span>

 <span data-ttu-id="e3102-117">Metoda **String. TrimEnd** usuwa znaki z końca ciągu, tworząc nowy obiekt ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="e3102-118">Tablica znaków jest przenoszona do tej metody w celu określenia znaków do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e3102-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="e3102-119">Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="e3102-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="e3102-120">Przycinanie zostaje zatrzymane, gdy zostanie znaleziony znak nieokreślony w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e3102-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="e3102-121">Poniższy przykład usuwa ostatnie litery ciągu przy użyciu metody **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="e3102-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="e3102-122">W tym przykładzie pozycja znaku `'r'` i znaku `'W'` są odwracane w celu zilustrowania, że kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="e3102-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="e3102-123">Zauważ, że ten kod usuwa ostatni wyraz `MyString` i część pierwszej.</span><span class="sxs-lookup"><span data-stu-id="e3102-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="e3102-124">Ten kod wyświetla `He` konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="e3102-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="e3102-125">Poniższy przykład usuwa ostatni wyraz ciągu przy użyciu metody **TrimEnd** .</span><span class="sxs-lookup"><span data-stu-id="e3102-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="e3102-126">W tym kodzie przecinek następuje po słowie `Hello` i, ponieważ przecinek nie jest określony w tablicy znaków do przycinania, przycinanie następuje w przecinek.</span><span class="sxs-lookup"><span data-stu-id="e3102-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="e3102-127">Ten kod wyświetla `Hello,` konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="e3102-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="e3102-128">Metoda TrimStart</span><span class="sxs-lookup"><span data-stu-id="e3102-128">TrimStart</span></span>

 <span data-ttu-id="e3102-129">Metoda **String. TrimStart** jest podobna do metody **String. TrimEnd** , z tą różnicą, że tworzy nowy ciąg przez usunięcie znaków z początku istniejącego obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="e3102-130">Tablica znaków jest przenoszona do metody **TrimStart** w celu określenia znaków do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e3102-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="e3102-131">Podobnie jak w przypadku metody **TrimEnd** , kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="e3102-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="e3102-132">Przycinanie zostaje zatrzymane, gdy zostanie znaleziony znak nieokreślony w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e3102-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="e3102-133">Poniższy przykład usuwa pierwsze słowo ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="e3102-134">W tym przykładzie pozycja znaku `'l'` i znaku `'H'` są odwracane w celu zilustrowania, że kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="e3102-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="e3102-135">Ten kod wyświetla `World!` konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="e3102-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="e3102-136">Usuń</span><span class="sxs-lookup"><span data-stu-id="e3102-136">Remove</span></span> 

 <span data-ttu-id="e3102-137">Metoda <xref:System.String.Remove%2A?displayProperty=nameWithType> usuwa określoną liczbę znaków, zaczynając od określonej pozycji w istniejącym ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="e3102-138">Ta metoda przyjmuje indeks oparty na wartości zero.</span><span class="sxs-lookup"><span data-stu-id="e3102-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="e3102-139">Poniższy przykład usuwa dziesięć znaków z ciągu, zaczynając od pozycji piątej indeksu ciągu od zera.</span><span class="sxs-lookup"><span data-stu-id="e3102-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="e3102-140">stępować</span><span class="sxs-lookup"><span data-stu-id="e3102-140">Replace</span></span>

 <span data-ttu-id="e3102-141">Można również usunąć określony znak lub podciąg z ciągu, wywołując metodę <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> i określając pusty ciąg (<xref:System.String.Empty?displayProperty=nameWithType>) jako zamiennik.</span><span class="sxs-lookup"><span data-stu-id="e3102-141">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="e3102-142">Poniższy przykład usuwa wszystkie przecinki z ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3102-142">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e3102-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3102-143">See also</span></span>

- [<span data-ttu-id="e3102-144">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="e3102-144">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
