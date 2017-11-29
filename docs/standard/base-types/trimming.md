---
title: "Przycinanie i usuwanie znaków z ciągów w .NET"
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
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fde24a97234d275d3d599f13bfc4063af939507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="d348c-102">Przycinanie i usuwanie znaków z ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="d348c-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="d348c-103">Jeśli analizy zdanie w poszczególnych wyrazów może być na końcu wyrazy, które mają puste miejsca (nazywane również spacji) na dowolnym jej końcu słowo.</span><span class="sxs-lookup"><span data-stu-id="d348c-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="d348c-104">W takiej sytuacji można użyć jednej z metod przycinania w **System.String** klasę, aby usunąć dowolną liczbę spacji ani innych znaków od określonej pozycji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="d348c-105">W poniższej tabeli opisano dostępne metody przycinania.</span><span class="sxs-lookup"><span data-stu-id="d348c-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="d348c-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="d348c-106">Method name</span></span>|<span data-ttu-id="d348c-107">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="d348c-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="d348c-108">Usuwa spacji ani znaków określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="d348c-109">Usuwa określone w tablicy znaków od końca ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="d348c-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="d348c-110">Usuwa określone w tablicy znaków od początku ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="d348c-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="d348c-111">Usuwa określoną liczbę znaków od pozycji określony indeks, w ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="d348c-112">TRIM</span><span class="sxs-lookup"><span data-stu-id="d348c-112">Trim</span></span>  
 <span data-ttu-id="d348c-113">Można łatwo usunąć spacji z obydwu końców ciąg, przy użyciu <xref:System.String.Trim%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d348c-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="d348c-114">Można również usunąć znaki określone w tablicy znaków od początku i końca ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="d348c-115">Poniższy przykład usuwa białe znaki, kropek i gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="d348c-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="d348c-116">Metoda TrimEnd</span><span class="sxs-lookup"><span data-stu-id="d348c-116">TrimEnd</span></span>  
 <span data-ttu-id="d348c-117">**String.TrimEnd** metoda usuwa znaków od końca ciągu, utworzenie nowego obiektu ciąg.</span><span class="sxs-lookup"><span data-stu-id="d348c-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="d348c-118">Tablicy znaków jest przekazywany do tej metody, aby określić znaków ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="d348c-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="d348c-119">Kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="d348c-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="d348c-120">Przycinanie zatrzymywana, gdy znajduje się znak nie jest określone w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d348c-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="d348c-121">Poniższy przykład umożliwia usunięcie ostatniego litery przy użyciu ciągu **TrimEnd** metody.</span><span class="sxs-lookup"><span data-stu-id="d348c-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="d348c-122">W tym przykładzie, pozycja `'r'` znaków i `'W'` znak są wycofywane w celu zilustrowania kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="d348c-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="d348c-123">Zwróć uwagę, że ten kod usuwa wyrazu ostatnich `MyString` plus część pierwszy.</span><span class="sxs-lookup"><span data-stu-id="d348c-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="d348c-124">Ten kod wyświetla `He` do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d348c-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="d348c-125">Poniższy przykład umożliwia usunięcie ostatniego wyrazu przy użyciu ciągu **TrimEnd** metody.</span><span class="sxs-lookup"><span data-stu-id="d348c-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="d348c-126">W tym kodzie przecinek następuje wyraz `Hello` i ponieważ przecinek nie jest określone w tablicy znaków, aby przyciąć, przycinanie kończy się po przecinku.</span><span class="sxs-lookup"><span data-stu-id="d348c-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="d348c-127">Ten kod wyświetla `Hello,` do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d348c-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="d348c-128">Metoda TrimStart</span><span class="sxs-lookup"><span data-stu-id="d348c-128">TrimStart</span></span>  
 <span data-ttu-id="d348c-129">**String.TrimStart** metoda jest podobna do **String.TrimEnd** metody, ale tworzy nowy ciąg przez usunięcie znaków od początku z istniejącym obiektem ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="d348c-130">Tablicy znaków jest przekazywana do **TrimStart** metodę, aby określić znaków ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="d348c-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="d348c-131">Jak **TrimEnd** metody, kolejność elementów w tablicy znaków nie ma wpływu na operację przycinania.</span><span class="sxs-lookup"><span data-stu-id="d348c-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="d348c-132">Przycinanie zatrzymywana, gdy znajduje się znak nie jest określone w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d348c-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="d348c-133">Poniższy przykład umożliwia usunięcie pierwsze słowo ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="d348c-134">W tym przykładzie, pozycja `'l'` znaków i `'H'` znak są wycofywane w celu zilustrowania kolejność znaków w tablicy nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="d348c-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="d348c-135">Ten kod wyświetla `World!` do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d348c-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="d348c-136">Usuń</span><span class="sxs-lookup"><span data-stu-id="d348c-136">Remove</span></span>  
 <span data-ttu-id="d348c-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda usuwa określoną liczbę znaków, zaczynające się od określonej pozycji w ciągu istniejących.</span><span class="sxs-lookup"><span data-stu-id="d348c-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="d348c-138">Ta metoda przyjmuje liczony od zera indeks.</span><span class="sxs-lookup"><span data-stu-id="d348c-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="d348c-139">Poniższy przykład umożliwia usunięcie 10 znaków od początku ciągu, w pozycji pięciu liczony od zera indeksu ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="d348c-140">Można również usunąć określony znak lub podciąg z ciągu wywołując <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> — metoda i określając pustego ciągu (<xref:System.String.Empty?displayProperty=nameWithType>) do zamiany.</span><span class="sxs-lookup"><span data-stu-id="d348c-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="d348c-141">Poniższy przykład umożliwia usunięcie wszystkich przecinkami z ciągu.</span><span class="sxs-lookup"><span data-stu-id="d348c-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="d348c-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d348c-142">See Also</span></span>  
 [<span data-ttu-id="d348c-143">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="d348c-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
