---
title: Operacje ciągu podstawowego w programie .NET
description: Dowiedz się więcej o podstawowych operacjach, które można wykonać na ciągach.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132912"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="22204-103">Operacje ciągu podstawowego w programie .NET</span><span class="sxs-lookup"><span data-stu-id="22204-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="22204-104">Aplikacje często odpowiadają użytkownikom, tworząc wiadomości na podstawie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="22204-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="22204-105">Na przykład nie jest rzadkością dla witryn sieci Web, aby odpowiedzieć na nowo zalogowanego użytkownika z wyspecjalizowanym powitaniem, który zawiera nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="22204-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="22204-106">Kilka metod w <xref:System.String?displayProperty=nameWithType> <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasach i umożliwiają dynamiczne konstruowanie ciągów niestandardowych do wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="22204-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="22204-107">Metody te pomagają również wykonać szereg podstawowych operacji ciągu, takich jak tworzenie nowych ciągów z tablic bajtów, porównywanie wartości ciągów i modyfikowanie istniejących ciągów.</span><span class="sxs-lookup"><span data-stu-id="22204-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22204-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="22204-108">In This Section</span></span>  
 [<span data-ttu-id="22204-109">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="22204-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="22204-110">Opisuje podstawowe sposoby konwertowania obiektów na ciągi i łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="22204-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="22204-111">Przycinanie i usuwanie znaków</span><span class="sxs-lookup"><span data-stu-id="22204-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="22204-112">W tym artykule opisano sposób przycinania lub usuwania znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="22204-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="22204-113">Uzupełnianie ciągów</span><span class="sxs-lookup"><span data-stu-id="22204-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="22204-114">Opisuje sposób wstawiania znaków lub pustych spacji do ciągu.</span><span class="sxs-lookup"><span data-stu-id="22204-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="22204-115">Porównywanie ciągów</span><span class="sxs-lookup"><span data-stu-id="22204-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="22204-116">Opisuje sposób porównywania zawartości dwóch lub więcej ciągów.</span><span class="sxs-lookup"><span data-stu-id="22204-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="22204-117">Zmienianie wielkości liter</span><span class="sxs-lookup"><span data-stu-id="22204-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="22204-118">Opisuje sposób zmiany przypadku znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="22204-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="22204-119">Używanie klasy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="22204-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="22204-120">Opisuje sposób tworzenia i modyfikowania <xref:System.Text.StringBuilder> dynamicznych obiektów ciągu z klasą.</span><span class="sxs-lookup"><span data-stu-id="22204-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="22204-121">Porady: wykonywanie podstawowych działań na ciągach</span><span class="sxs-lookup"><span data-stu-id="22204-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="22204-122">Demonstruje użycie podstawowych operacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="22204-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="22204-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="22204-123">Related Sections</span></span>  
 [<span data-ttu-id="22204-124">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="22204-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="22204-125">Opisuje sposób konwertowania jednego typu na inny typ.</span><span class="sxs-lookup"><span data-stu-id="22204-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="22204-126">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="22204-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="22204-127">W tym artykule opisano sposób formatowania ciągów za pomocą specyfikatorów formatów.</span><span class="sxs-lookup"><span data-stu-id="22204-127">Describes how to format strings using format specifiers.</span></span>
