---
title: Podstawowe operacje na ciągach w programie .NET
description: Zapoznaj się z podstawowymi operacjami, które można wykonywać na ciągach.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132912"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="4cfe5-103">Podstawowe operacje na ciągach w programie .NET</span><span class="sxs-lookup"><span data-stu-id="4cfe5-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="4cfe5-104">Aplikacje często odpowiadają użytkownikom przez konstruowanie komunikatów na podstawie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="4cfe5-105">Na przykład nierzadko zdarza się, aby witryny sieci Web odpowiadały nowo zalogowanemu użytkownikowi z wyspecjalizowanym powitaniem zawierającym nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="4cfe5-106">Kilka metod klasy <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> umożliwia dynamiczne konstruowanie ciągów niestandardowych do wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="4cfe5-107">Te metody ułatwiają również wykonywanie wielu podstawowych operacji na ciągach, takich jak tworzenie nowych ciągów z tablic bajtów, porównywanie wartości ciągów i modyfikowanie istniejących ciągów.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cfe5-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4cfe5-108">In This Section</span></span>  
 [<span data-ttu-id="4cfe5-109">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="4cfe5-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="4cfe5-110">Opisuje podstawowe sposoby konwersji obiektów na ciągi i łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="4cfe5-111">Przycinanie i usuwanie znaków</span><span class="sxs-lookup"><span data-stu-id="4cfe5-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="4cfe5-112">Opisuje sposób przycinania lub usuwania znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="4cfe5-113">Uzupełnianie ciągów</span><span class="sxs-lookup"><span data-stu-id="4cfe5-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="4cfe5-114">Opisuje, w jaki sposób wstawiać znaki lub puste spacje do ciągu.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="4cfe5-115">Porównywanie ciągów</span><span class="sxs-lookup"><span data-stu-id="4cfe5-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="4cfe5-116">Opisuje sposób porównywania zawartości dwóch lub więcej ciągów.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="4cfe5-117">Zmienianie wielkości liter</span><span class="sxs-lookup"><span data-stu-id="4cfe5-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="4cfe5-118">Opisuje sposób zmiany wielkości liter w ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="4cfe5-119">Używanie klasy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="4cfe5-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="4cfe5-120">Opisuje sposób tworzenia i modyfikowania dynamicznych obiektów ciągów z klasą <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="4cfe5-121">Instrukcje: Wykonywanie podstawowych działań na ciągach</span><span class="sxs-lookup"><span data-stu-id="4cfe5-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="4cfe5-122">Demonstruje użycie podstawowych operacji na ciągach.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4cfe5-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4cfe5-123">Related Sections</span></span>  
 [<span data-ttu-id="4cfe5-124">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="4cfe5-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="4cfe5-125">Opisuje sposób konwersji jednego typu na inny typ.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="4cfe5-126">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="4cfe5-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="4cfe5-127">Opisuje sposób formatowania ciągów przy użyciu specyfikatorów formatu.</span><span class="sxs-lookup"><span data-stu-id="4cfe5-127">Describes how to format strings using format specifiers.</span></span>
