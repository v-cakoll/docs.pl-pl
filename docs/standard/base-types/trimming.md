---
title: Przycinanie i usuwanie znaków z ciągów w .NET
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
ms.openlocfilehash: 02704ed5e396e973101bab4e5306d81f5a169d0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569892"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="7a4df-102">Przycinanie i usuwanie znaków z ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="7a4df-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="7a4df-103">Jeśli analizy zdanie w poszczególnych wyrazów może być na końcu wyrazy, które mają puste miejsca (nazywane również spacji) na dowolnym jej końcu słowo.</span><span class="sxs-lookup"><span data-stu-id="7a4df-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="7a4df-104">W takiej sytuacji można użyć jednej z metod przycinania w **System.String** klasę, aby usunąć dowolną liczbę spacji ani innych znaków od określonej pozycji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="7a4df-105">W poniższej tabeli opisano dostępne metody przycinania.</span><span class="sxs-lookup"><span data-stu-id="7a4df-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="7a4df-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="7a4df-106">Method name</span></span>|<span data-ttu-id="7a4df-107">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="7a4df-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="7a4df-108">Usuwa spacji ani znaków określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="7a4df-109">Usuwa określone w tablicy znaków od końca ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="7a4df-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="7a4df-110">Usuwa określone w tablicy znaków od początku ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="7a4df-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="7a4df-111">Usuwa określoną liczbę znaków od pozycji określony indeks, w ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="7a4df-112">TRIM</span><span class="sxs-lookup"><span data-stu-id="7a4df-112">Trim</span></span>  
 <span data-ttu-id="7a4df-113">Można łatwo usunąć spacji z obydwu końców ciąg, przy użyciu <xref:System.String.Trim%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7a4df-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="7a4df-114">Można również usunąć znaki określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="7a4df-115">Poniższy przykład usuwa białe znaki, kropek i gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="7a4df-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="7a4df-116">Metoda TrimEnd</span><span class="sxs-lookup"><span data-stu-id="7a4df-116">TrimEnd</span></span>  
 <span data-ttu-id="7a4df-117">**String.TrimEnd** metoda usuwa znaków od końca ciągu, utworzenie nowego obiektu ciąg.</span><span class="sxs-lookup"><span data-stu-id="7a4df-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="7a4df-118">Tablicy znaków jest przekazywany do tej metody, aby określić znaków ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="7a4df-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="7a4df-119">Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="7a4df-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="7a4df-120">Przycinanie zatrzymywana, gdy znajduje się znak nie jest określone w tablicy.</span><span class="sxs-lookup"><span data-stu-id="7a4df-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="7a4df-121">Poniższy przykład umożliwia usunięcie ostatniego litery przy użyciu ciągu **TrimEnd** metody.</span><span class="sxs-lookup"><span data-stu-id="7a4df-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="7a4df-122">W tym przykładzie, pozycja `'r'` znaków i `'W'` znak są wycofywane w celu zilustrowania kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="7a4df-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="7a4df-123">Zwróć uwagę, że ten kod usuwa wyrazu ostatnich `MyString` plus część pierwszy.</span><span class="sxs-lookup"><span data-stu-id="7a4df-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="7a4df-124">Ten kod wyświetla `He` do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a4df-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="7a4df-125">Poniższy przykład umożliwia usunięcie ostatniego wyrazu przy użyciu ciągu **TrimEnd** metody.</span><span class="sxs-lookup"><span data-stu-id="7a4df-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="7a4df-126">W tym kodzie przecinek następuje wyraz `Hello` i ponieważ przecinek nie jest określone w tablicy znaków, aby przyciąć, przycinanie kończy się po przecinku.</span><span class="sxs-lookup"><span data-stu-id="7a4df-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="7a4df-127">Ten kod wyświetla `Hello,` do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a4df-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="7a4df-128">Metoda TrimStart</span><span class="sxs-lookup"><span data-stu-id="7a4df-128">TrimStart</span></span>  
 <span data-ttu-id="7a4df-129">**String.TrimStart** metoda jest podobna do **String.TrimEnd** metody, ale tworzy nowy ciąg przez usunięcie znaków od początku z istniejącym obiektem ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="7a4df-130">Tablicy znaków jest przekazywana do **TrimStart** metodę, aby określić znaków ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="7a4df-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="7a4df-131">Jak **TrimEnd** metody, kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="7a4df-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="7a4df-132">Przycinanie zatrzymywana, gdy znajduje się znak nie jest określone w tablicy.</span><span class="sxs-lookup"><span data-stu-id="7a4df-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="7a4df-133">Poniższy przykład umożliwia usunięcie pierwsze słowo ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="7a4df-134">W tym przykładzie, pozycja `'l'` znaków i `'H'` znak są wycofywane w celu zilustrowania kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="7a4df-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="7a4df-135">Ten kod wyświetla `World!` do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a4df-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="7a4df-136">Usuń</span><span class="sxs-lookup"><span data-stu-id="7a4df-136">Remove</span></span>  
 <span data-ttu-id="7a4df-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda usuwa określoną liczbę znaków, zaczynające się od określonej pozycji w ciągu istniejących.</span><span class="sxs-lookup"><span data-stu-id="7a4df-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="7a4df-138">Ta metoda przyjmuje liczony od zera indeks.</span><span class="sxs-lookup"><span data-stu-id="7a4df-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="7a4df-139">Poniższy przykład umożliwia usunięcie 10 znaków od początku ciągu, w pozycji pięciu liczony od zera indeksu ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="7a4df-140">Można również usunąć określony znak lub podciąg z ciągu wywołując <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> — metoda i określając pustego ciągu (<xref:System.String.Empty?displayProperty=nameWithType>) do zamiany.</span><span class="sxs-lookup"><span data-stu-id="7a4df-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="7a4df-141">Poniższy przykład umożliwia usunięcie wszystkich przecinkami z ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a4df-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="7a4df-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a4df-142">See Also</span></span>  
 [<span data-ttu-id="7a4df-143">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="7a4df-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
