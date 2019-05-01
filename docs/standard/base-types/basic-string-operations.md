---
title: Podstawowe operacje na ciągach w programie .NET
description: Poznaj podstawowe operacje, które można wykonywać na ciągi.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
author: rpetrusha
ms.author: ronpet
ms.custom: seadec18
ms.openlocfilehash: 8621e79ad6e305f3859dc269965ecd216081f695
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936815"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="a27f6-103">Podstawowe operacje na ciągach w programie .NET</span><span class="sxs-lookup"><span data-stu-id="a27f6-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="a27f6-104">Aplikacje często odpowiadają użytkownikom tworząc wiadomości, w oparciu o dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a27f6-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="a27f6-105">Na przykład nie jest niczym niezwykłym dla witryn sieci Web odpowiedzieć na nowo zalogowanego użytkownika przy użyciu wyspecjalizowanego powitanie, które zawiera nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a27f6-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="a27f6-106">Kilka metod w <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy umożliwiają dynamicznie utworzyć niestandardowe ciągi do wyświetlenia w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a27f6-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="a27f6-107">Te metody także pomóc wykonywać podstawowe operacje na ciągach takich jak tworzenie nowych ciągów w tablice bajtów, porównywania wartości ciągów i modyfikowanie istniejących ciągów.</span><span class="sxs-lookup"><span data-stu-id="a27f6-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a27f6-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a27f6-108">In This Section</span></span>  
 [<span data-ttu-id="a27f6-109">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="a27f6-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="a27f6-110">W tym artykule opisano podstawowe sposoby Konwertowanie obiektów na ciągi i łączyć ciągi.</span><span class="sxs-lookup"><span data-stu-id="a27f6-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="a27f6-111">Przycinanie i usuwanie znaków</span><span class="sxs-lookup"><span data-stu-id="a27f6-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="a27f6-112">Opisuje sposób trim lub usuń znaki w ciągu.</span><span class="sxs-lookup"><span data-stu-id="a27f6-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="a27f6-113">Uzupełnianie ciągów</span><span class="sxs-lookup"><span data-stu-id="a27f6-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="a27f6-114">W tym artykule opisano sposób wstawiania znaków ani spacji pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="a27f6-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="a27f6-115">Porównywanie ciągów</span><span class="sxs-lookup"><span data-stu-id="a27f6-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="a27f6-116">W tym artykule opisano, jak porównywanie zawartości dwóch lub więcej ciągów.</span><span class="sxs-lookup"><span data-stu-id="a27f6-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="a27f6-117">Zmienianie wielkości liter</span><span class="sxs-lookup"><span data-stu-id="a27f6-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="a27f6-118">W tym artykule opisano, jak zmienić wielkość liter w ciągu.</span><span class="sxs-lookup"><span data-stu-id="a27f6-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="a27f6-119">Używanie klasy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="a27f6-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="a27f6-120">W tym artykule opisano sposób tworzenia i modyfikowania obiektów dynamicznych parametrów za pomocą <xref:System.Text.StringBuilder> klasy.</span><span class="sxs-lookup"><span data-stu-id="a27f6-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="a27f6-121">Instrukcje: Wykonywania podstawowych działań na ciągach</span><span class="sxs-lookup"><span data-stu-id="a27f6-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="a27f6-122">Zademonstrowano użycie podstawowe operacje na ciągach.</span><span class="sxs-lookup"><span data-stu-id="a27f6-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a27f6-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a27f6-123">Related Sections</span></span>  
 [<span data-ttu-id="a27f6-124">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="a27f6-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="a27f6-125">W tym artykule opisano sposób konwertowania z jednego typu do innego typu.</span><span class="sxs-lookup"><span data-stu-id="a27f6-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="a27f6-126">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="a27f6-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="a27f6-127">W tym artykule opisano sposób formatowania ciągów przy użyciu specyfikatorów formatu.</span><span class="sxs-lookup"><span data-stu-id="a27f6-127">Describes how to format strings using format specifiers.</span></span>
